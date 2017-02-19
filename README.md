# Tech review checklist (WIP)

tl;dr This is a document evolved from a talking point checklist made by [Teijo](https://github.com/teijo) and [Lauri](https://github.com/laurilehmijoki). The original checklist was used as a quick baseline in technical evaluation interviews of software projects. This is not an exhaustive list, it's a way to get started and have basic structure for things to cover.

The goal of the checklist is to ensure that any high level**technical** area of a project has not been overlooked, and that concerns possibly existing at the time of the review have either been acknowledged or become answered over the review. The list **does not** consider things such as business viability which is even **more important** in the grand scheme of things. Even though not purely technical topic, the roles and interactions with project end-users, non-technical team members, and stakeholders should be understood as it affects the projects' behaviour.

If a specific item does not apply to the project at the moment, **understand why**. "Correct" answers are not fixed, as long as choices make sense and consequences have been understood. The impact of some items **becoming relevant later** should be understood.

Things to keep in mind

- Personnel: ownership, vision, skills, conventions, scaling, turnover, ...
- Development: maintainability, modularity, right tool for each job, ...
- Operational: breakdowns, scaling, attacks, ...
- Legal: audit trail, personal data storage, ...


## The checklist

- **General**
    - Background for the project
        - How long it has been running
        - How many people, team composition, hierarchy
    - Get a short end-user demo
    - What's needed to take a feature into production
    - Big picture with all relevant high level components (databases / storage, backend applications, clients, integrations)
    - Past, current and foreseeable technical challenges

- **Technologies**
    - Programming languages
        - Tool chain for each
    - Used major libraries
    - Frameworks
    - Maturity of the choices
    - Reasoning for major technology picks

- **Architecture**
    - Where is the state?
    - Persistence (databases, file systems, …)
        - Which main features are used
        - What is purpose of each system (e.g. Redis, Elasticsearch, PostgreSQL, S3, ...)
        - Scaling strategy (sharding, master-slave, caching, …)
        - Backups
        - Caching (layers, invalidation, CDN, ...)
        - Fail tolerance (stand-by, multi-master, quorum, …)
        - RDBMS / NoSQL schema upgrades (manual, automatic, …)
            - Where is schema stored e.g. if new DB environment is set up
    - Client design
        - Portability
        - Amount of business logic in client (is backend API fit 100% or does client need to combine data sources)
    - Backend design
        - Monolith or (micro) service oriented
        - Could new clients be added easily
            - Is there e.g. a clear REST API
        - Persistence integration (does each DB have single owner application)
    - Out-of-the-box servers / applications / services
        - How do they integrate to rest of the system
        - How are integrations tested / mocked?

- **Maintenance and evolution**
    - Testing
        - What technologies
        - End-to-end (from client to persistence layer and back)
        - Manual testing
        - Unit testing
    - Build process
        - Artefact types (ZIP, Docker image, JAR, …)
        - Artefact versioning and storage (Artifactory, Docker repo, disk, …)
    - What manual steps, if any, are required for production update

- **Operations**
    - Environmants (dev, test, qa, production, ...)
        - How do environments differ from each other
        - How close to production is local development environment
    - Infrastructure
        - Host type (cloud, dedicated, managed (Heroku, Kubernetes, ...))
        - Is deployment portable to different environments
        - Load balancing
        - Firewalls / routing
        - Multiple availability zones / regional distribution
        - Scaling
            - Which parts of the system can be duplicated
            - Which parts cannot, is it possible to change this?
    - Deployment
        - Mutable vs. immutable servers or applications
        - Provisioning tool (Ansible, Chef, Puppet, shell script, …)
        - Key management
            - Sharing among developers
            - Encryption
    - System monitoring
        - Logging
            - Centralized or distributed
            - Audit logging
        - Performance metrics
            - How do you detect performance issues
            - Long term trends
        - Availability
            - External monitoring
            - Internal monitoring
        - How do you know there is a problem (radiator, email, sms, …)
        - Are errors collected (client errors, backend errors, stack traces, exit codes, ...)

- **Ways of working**
    - How many people in team, how many are somehow part of the development cycle (coding, ux, graphics, …)
    - Development process (Scrum, Kanban, Waterfall…)
    - Where is code stored
        - How is code split to repositories?
        - Where are configurations stored?

- **Quality assurance**
    - Bug tracking
    - CI setup
        - Is there one at all
        - What gets done before a deployable build ready
            - Tests run before release / build
            - Are static analysis tools used
        - Is deployment done over CI (at least to test/integration env)
    - Load testing


## Definitions

More detailed explanations for the items in the list that are not self-explanatory.

TBD
