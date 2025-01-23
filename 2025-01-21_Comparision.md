Microsoft SDL
https://www.microsoft.com/en-us/securityengineering/sdl/practices?oneroute=true
    1. Establish security standards, metrics, and governance
        1.1 Identify Required Standards
        1.2 Define Security Requirements – Establish a minimum-security baseline that takes account of both security and compliance controls. Ensure these are baked into the DevOps process and pipeline. At the very minimum, ensure the baseline takes into account real-world threats such as the OWASP Top 10 or SANS Top 25, and industry or regulatory requirements and issues known to exist or that could be introduced by human error in the technology stack you select. Use Azure DevOps to help record security requirements once defined:
        1.3 Define metrics and compliance reporting – It is essential to define the minimum acceptable levels of security quality and to hold engineering teams accountable to meeting that criteria. Defining these early helps a team understand risks associated with security issues, identify and fix security defects during development, and apply the standards throughout the entire project. Setting a meaningful bug bar involves clearly defining the severity thresholds of security vulnerabilities (for example, all known vulnerabilities discovered with a “critical” or “important” severity rating must be fixed with a specified time frame) and never relaxing it once it's been set. The bug bar should be maintained to reflect the changing threat landscape, both the type of issue and their severity. The bug bar is a great way to ensure that everyone involved in triaging issues understands why a security issue has a certain severity and what action is required.
        1.4 Create a Security Exception Process
    2. Require use of proven security features, languages, and frameworks
        2.1 Identity - Ensure users are using strong authentication and only have the level of permissions suitable to their needs (least privilege). See Practice 6.1 Take a Zero Trust Approach for more information.
        2.2 AI safety and security - Review the specific guidance for anyone building or integrating AI solutions:
        2.3 Data protection: Securing content used in apps - Secure implementation and connection to databases, storage accounts, unstructured documents, and more.
        2.4 Logging and telemetry - Provides valuable insights into the behavior and performance of systems and applications. Security logging must be enabled and retained to assist with any post-incident investigations. Telemetry helps guide developer feedback on user interaction, feature popularity, and performance metrics.
        2.5 Use approved tools - Define and publish a list of approved tools and their associated security checks, such as compiler/linker options and warnings. Engineers should strive to use the latest version of approved tools, such as compiler versions, and to take advantage of new security analysis functionality and protections.
    3. Perform security design review and threat modeling
        3.1 Identify use cases, scenarios, and assets - An essential part of threat modeling and reviewing threat models is understanding what business functions or “use cases” the system has. Scenarios describing the sequence of steps for typical interactions with the system illustrate its intended purposes and workflows. They also describe the different roles of users and external systems that connect to it. The first step in threat modeling is to document the business functions the system performs and how users or other systems interact with it. Supplement textual descriptions of use cases and scenarios with flowcharts and UML sequence diagrams as needed. Whether you use formal documentation such as use cases and scenarios, or take a more informal approach, ensure you provide context that answers these questions:
        3.2 Create an architecture overview - In addition to documenting business functionality and assets, create diagrams and tables to depict the architecture of your application, including subsystems, trust boundaries, and data flows between actors and components. At minimum, a Data Flow Diagram (DFD) is recommended, and other supplementary diagrams such as UML Sequence Diagrams to illustrate complex flows may also be helpful. A DFD is a high-level way to visualize data flows between the major components of a system. It is a simplified view that does not include every detail—just enough to understand the security properties and attack surface of the system. It is a recommended practice to label the following in your DFD arrows:
        3.3  Identify the threats – Threat modeling is most effective when performed by a group of people familiar with the system architecture and business functions who are prepared to think like attackers. Here are some tips for scheduling an effective threat modeling session:
        3.4 Identify and track mitigations - Secure Design Philosophy: When identifying mitigations, keep in mind that security is not “all or nothing”. A partial mitigation that raises the cost for an attacker, slows them down to give defenders time to detect them, or limits the scope of damage is much better than no mitigation at all. Think in terms of layered defenses. Attackers don’t just exploit a single vulnerability and stop there. They chain multiple vulnerabilities together, pivoting from one target system to the next until they achieve their objective (or get caught.) Each layered defense increases the likelihood that attackers will be blocked or detected. Also, assume that other layers’ security controls will be bypassed or disabled. This is the essence of the Assume Breach philosophy which results in a resilient set of layered defenses rather than relying solely on external defenses that, if bypassed, result in a major breach.
        3.5 Communicate threat models to key stakeholders - Threat modeling is not complete until you create work items to track your threat findings and the related development and testing tasks to mitigate them. Consider tagging the work items and writing queries so they are easy to find. A threat model provides the seeds for a good security test plan. Be sure to test that your mitigations work as intended and use automated testing when possible.
        3.6 Threat Modeling resources
    4. Define and use cryptography standards
        4.1 Encrypt data in transit and at rest - Ensure data is encrypted at rest and in transit, this includes security-sensitive information and management and control data. For encryption in transit, use only strong versions of TLS (see recommendation) for all internet traffic and ideally, traffic within private networks. For encryption at rest, be sure you understand the protections an encryption solution provides. While many easily deployable encryption solutions exist to protect data on a device or disk from theft (offline attack), they do not protect against online compromise through application logic, and additional solutions are required in these situations to encrypt data before it's written to storage (encrypt in transit).
        4.2 Post-Quantum Cryptography (PQC) - We recommend prioritizing symmetric encryption where applicable and subsequently adopting post-quantum cryptography (PQC) for asymmetric encryption once standardized and approved by relevant setting bodies and governments, as recommended by cybersecurity agencies globally.
        4.3 Cryptographic agility - The practice of implementing cryptographic solutions to enable changes to new cryptographic mechanisms, algorithms and libraries when the need arises, such as in the case of vulnerabilities discovered in libraries that compromise sound algorithms, or when an encryption algorithm might be considered broken at any time. Cryptographic agility is critical to any successful plan to efficiently apply new cryptographic updates, including the adoption of quantum-safe algorithms.
        4.4 Encryption key and certificate management and rotation - Encrypting data is only a portion of a successful cryptography standard and it's also essential to define how to manage, protect and rotate encryption keys and certificates. Keys and certificates have a limited lifespan, and it is necessary to define mechanisms to manage the lifecycle of keys and certificates, including mechanisms to both create new keys and certificates once the previous ones are near expiration and to rapidly rotate in the event of a security incident, such as unintended access. Anyone who can access an encryption key or private key can access the encrypted data, and therefore it's necessary to control who (whether a person or a service) has access (see Practice 2.1 Identity) and provide a clear audit log of that access (see Practice 2.5 Use approved tools).
    5. Secure the software supply chain
        5.1 Establish a secure open source software ingestion process - The Secure Supply Chain Consumption Framework (S2C2F) is a security assurance and risk reduction process that is focused on securing how developers consume open source software.
        5.2 Understand dependencies in your environment - Many software projects depend on open-source software projects, and many of these have dependencies on other open source projects. It’s essential to inventory use of open source, including dependencies to be able to update these if a vulnerability is discovered.
        5.3 Produce software bill of materials (SBOM) - SBOMs contribute software transparency and integrity. An SBOM is a machine-readable document that lists all of the components, including open source components used to create a product and helps better inventory software and therefore helps organizations to understand license and vulnerability risk. SBOMs also contain package and file checksums to help validate hashes, which is useful when signatures aren’t provided by other means.
        5.4 Signing and attesting artifacts – A Core aspect of software integrity is signing and validating its components. This applies to SBOMs just as much as artifacts created by tools integrated into your lifecycle, Artifact attestations establish a verifiable trail, enabling you to trace the integrity and prove the provenance of the artifact throughout the lifecycle.
    6. Secure the engineering environment
        6.1 Take a Zero Trust approach - At its core the Zero Trust model requires that each access request (user, service, or device) is verified as though it originated from an untrusted network, regardless of where the request originates or what resource it accesses. Base this always authenticate and authorize policy on all available data points, limit user access, especially privilede users, through Just-In-Time and Just-Enough-Access (JIT/JEA) policies and segment access to minimize the possible damage in the event of a breach.
        6.2 Disallow direct commits to production branches - Configure your source control repositories to prevent developer accounts from making direct commits to production branches and to require code review and approval for all pull requests. This ensures that a single compromised/rogue developer account cannot make arbitrary changes to code for production systems.
        6.3 Implement privileged access workstations - The use of hardened security workstations helps protect privileged users from internet attacks and threat vectors by providing a dedicated machine for sensitive tasks and separating these sensitive tasks and accounts from the daily use workstations.
        6.4 Provide Secure virtual workstations - Microsoft Dev Box gives developers self-service access to ready-to-code cloud workstations called dev boxes. Dev boxes can be configured with tools, source code, and prebuilt binaries that are specific to a project, so developers can immediately start working - securely. Dev boxes are managed like all devices on the network and can be more easily kept up to date and secured through security settings, network configuration and organizational policies.
        6.5 Implement GitHub Codespaces - Created with security in mind, Codespaces provides a secure development environment through its built-in capabilities and native integration with the GitHub platform. Developers can quickly spin up a Codespace with only an IDE or browser and a GitHub account and work in a shared and secure development environment.
        6.6 Secure deployment environments - Azure Deployment Environments empower development teams to quickly and easily spin up app infrastructure with project-based templates that establish consistency and best practices while maximizing security. This on-demand access to secure environments accelerates the stages of the software development lifecycle and compliments Microsoft Dev Box.
    7. Perform security testing
        7.1 Implement Static Analysis Security testing (SAST) - Analyzing the source code prior to compilation provides a highly scalable method of security code review and helps ensure that secure coding policies are being followed. It looks for known issues based on the application's logic and adherence to coding standards, rather than when the application is running. SAST is typically integrated into the developer workflow identifying simple to detect issues before code is committed and into build automation to identify vulnerabilities each time the software is built or packaged. There is no one- size-fits-all solution and development teams should decide the optimal frequency for performing SAST and will often deploy multiple tactics—to balance productivity with adequate security coverage.
        7.2 Implement dynamic analysis security testing (DAST) - Refers to testing a fully compiled, packaged an executing version of a program or service checks functionality that is only exercisable when all the components are integrated and running.  This is typically achieved using a tool or suite of prebuilt attacks or tools, often replicating in a limited form what an attacker might try, that specifically test application behavior for memory corruption, user privilege issues, and other critical security problems. Similar to SAST, there is no one-size-fits-all solution and while some tools, such as web app scanning tools, can be more readily integrated into the continuous integration / continuous delivery pipeline, other DAST testing such as fuzzing requires a different approach.
        7.3 Red/blue team exercises - A dedicated “red team” of security experts simulate real-world attacks at the network, platform, and application layers - challenging the ability of cloud services “blue team”, a dedicated team of security responders, to detect, protect against, and recover from security breaches. Every exercise is followed by full disclosure between the Red Team and Blue Team to identify gaps, address findings, and significantly improve breach response.
        7.4 Application penetration testing - Simulate real-world attacks and challenge teams to detect, protect, and recover. Penetration testing is a security analysis of a software system performed by skilled security professionals simulating the actions of a hacker. The objective of a penetration test is to uncover potential vulnerabilities resulting from coding errors, system configuration faults, or other operational deployment weaknesses, and as such the test typically finds the broadest variety of vulnerabilities. Penetration tests are often performed in conjunction with automated and manual code reviews to provide a greater level of analysis than would ordinarily be possible.
        7.5 Perform continuous security testing and measurement - Continuous security testing (CST) checks for security issues and unsafe implementations in third-party libraries on an ongoing basis. CST includes software composition analysis (SCA) checks and static application security testing (SAST).
        7.6 Perform triggered/cadence-based security testing - Routine security tests should be conducted at a regular cadence to meet compliance requirements. These tests should be conducted periodically and on schedule.
        7.7 Run a bug bounty program - A bug bounty program offers monetary rewards to ethical hackers to uncover significant vulnerabilities that have a direct and demonstrable impact on the systems.
    8. Ensure operational platform security
        8.1 Enforce multifactor authentication - It's often said, attackers don’t break-in, they sign-in and it’s therefore necessary to enforce additional controls to help protect all users, especially administrators.  Multifactor Authentication adds a critical second layer of security to sign-ins to help protect access to data and applications while still providing a simple and efficient sign-in experience.
        8.2 Protect administrative accounts - At Microsoft, a combination of layered defenses are used to protect administrative access to production systems, including Secure Admin Workstations (SAWs), alternate credentials with MFA for administration, and Just in Time privilege elevation (JIT) with role-based access control (RBAC). For more on how to do this see:
        8.3 Implement security baselines - All operational environments need to have security baselines defined and enforced. These can be created as policies that detect drift from configuration standards and implement automated remediation
        8.4 Create isolation layers - Isolation layers refers to the various levels at which security controls are applied to ensure that systems are kept separate and secure, across process, compute, and network.
        8.5 Use confidential compute -  Isolate sensitive data while it's being processed in the cloud. Since the dawn of cloud computing in Azure, we’ve recognized the crucial role of HBV in running customer workloads on VMs. However, VMs only protect the host machine from malicious activity within the VM. In many cases, a vulnerability in the VM interface could allow a bad actor to escape to the host, and from there they could fully access other customers’ VM. Confidential Compute presents a new layer of defense against these attacks by preventing bad actors with hosting environment access from accessing the content running in a VM. Our goal is to leverage Confidential VMs and Confidential Containers broadly across Azure Services, adding this extra layer of defense to VMs and containers utilized by our services. This has the potential to reduce the blast radius of a compromise at any level in Azure. While ambitious, one day using Confidential Compute should be as ubiquitous as other best practices have become such as encryption in transit or encryption at rest.
        8.6 Reduce the attack surface - Attack surfaces are all the places where your organization is vulnerable to cyberthreats and attacks.
        8.7 Perform platform penetration testing - Production running platform penetration testing, from physical data centers to cloud platforms.
        8.8 Implement operational terminals: device security - Microsoft has a privileged access strategy that guides on implementing secure accounts, workstations and devices and interface security. Device control is extremely important because an attacker with access to a device can impersonate users on it or steal credentials for future impersonation. For strongest security for highest impact assets and accounts, we recommend using privileged access workstation (PAW). This is the highest security configuration designed for extremely sensitive roles that would have a significant or material impact on the organization if their account was compromised. The PAW configuration includes security controls and policies that restrict local administrative access and productivity tools to minimize the attack surface to only what is absolutely required for performing sensitive job tasks. This makes the PAW device difficult for attackers to compromise because it blocks the most common vector for phishing attacks: email and web browsing. To provide productivity to these users, separate accounts and workstations must be provided for productivity applications and web browsing. While inconvenient, this is a necessary control to protect users whose account could inflict damage to most or all resources in the organization.
        8.9 Scheduled maintenance and automated patching cycles - All systems must be continuously monitored and updated with the latest security updates.
        8.10 Protect against DDoS attacks - Provide real-time mitigation to common network-level attacks. Distributed denial of service (DDoS) attacks are some of the largest availability and security concerns facing cloud applications, because any endpoint that's publicly reachable over the internet can be targeted. To address this, at a minimum traffic must be continually monitored and real-time mitigations must be provided for common network-level attacks. However, as DDoS attacks become more sophisticated and targeted, it may also be necessary to provide DDoS mitigations to protocol and application layer attacks.
    9. Implement security monitoring and response
        9.1 Proactively detect and address threats - Use a security analytics and threat intelligence platform to enable attack detection, threat visibility, proactive hunting, and threat response. This is often composed of extended detection and response (XDR) tools for well-known attacks, a security information and event management (SIEM) for building custom detections based on log files, and a Security Data Lake for long-term efficient storage of archival log files. A well-designed system for application, system, and security log files and other data sources is key to enable effective threat detection, investigation and forensic analysis, threat hunting, threat intelligence, and similar activities.
        9.2 Establish a standard incident response process – Preparing an Incident Response Plan is crucial for helping to address new threats that can emerge over time. It should be created in coordination with your organization’s dedicated Product Security Incident Response Team (PSIRT). The plan should include who to contact in case of a security emergency, and establish the protocol for security servicing, including plans for code inherited from other groups within the organization and for third-party code. The incident response plan should be tested before it is needed!
    10. Provide security training

SSDF
https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-218.pdf
    PO: Prepare the Organization
        PO.1: Define Security Requirements for Software Development
            PO.1.1: Identify and document all security requirements for the organization’s software development infrastructures and processes, and maintain the requirements over time.
            PO.1.2: Identify and document all security requirements for organization-developed software to meet, and maintain the requirements over time.
            PO.1.3: Communicate requirements to all third parties who will provide commercial software components to the organization for reuse by the organization’s own software. [Formerly PW.3.1]
        PO.2: Implement Roles and Responsibilities
            PO.2.1: Create new roles and alter responsibilities for existing roles as needed to encompass all parts of the SDLC. Periodically review and maintain the defined roles and responsibilities, updating them as needed.
            PO.2.2: Provide role-based training for all personnel with responsibilities that contribute to secure development. Periodically review personnel proficiency and role-based training, and update the training as needed.
            PO.2.3: Obtain upper management or authorizing official commitment to secure development, and convey that commitment to all with developmentrelated roles and responsibilities.
        PO.3: Implement Supporting Toolchains
            PO.3.1: Specify which tools or tool types must or should be included in each toolchain to mitigate identified risks, as well as how the toolchain components are to be integrated with each other.
            PO.3.2: Follow recommended security practices to deploy, operate, and maintain tools and toolchains.
            PO.3.3: Configure tools to generate artifacts6 of their support of secure software development practices as defined by the organization.
        PO.4: Define and Use Criteria for Software Security Checks
            PO.4.1: Define criteria for software security checks and track throughout the SDLC.
            PO.4.2: Implement processes, mechanisms, etc. to gather and safeguard the necessary information in support of the criteria.
        PO.5: Implement and Maintain Secure Environments for Software Development
            PO.5.1: Separate and protect each environment involved in software development.
            PO.5.2: Secure and harden development endpoints(i.e., endpoints for software designers, developers, testers, builders, etc.) to perform development-related tasks using a risk-based approach.
    PS(Protect the Software)
        PS.1: Protect All Forms of Code from Unauthorized Access and Tampering
            PS.1.1: Store all forms of code – including source code, executable code, and configuration-as-code – based on the principle of least privilege so that onlyauthorized personnel, tools, services, etc. have access.
        PS.2: Provide a Mechanism for Verifying Software Release Integrity
            PS.2.1: Make software integrity verification information available to software acquirers.
        PS.3: Archive and Protect Each Software Release
            PS.3.1: Securely archive the necessary files and supporting data (e.g., integrity verification information, provenance data) to be retained for each software release.
            PS.3.2: Collect, safeguard, maintain, and share provenance data for all components of each software release (e.g., in a software bill of materials [SBOM]).
    PW(Produce Well-Secured Software)
        PW.1: Design Software to Meet Security Requirements and Mitigate Security Risks
            PW.1.1: Use forms of risk modeling – such as threat modeling, attack modeling, or attack surface mapping – to help assess the security risk for the software.
            PW.1.2: Track and maintain the software’s security requirements, risks, and design decisions.
            PW.1.3: Where appropriate, build in support for using standardized security features and services (e.g., enabling software to integrate with existing log management, identity management, access control, and vulnerability management systems) instead of creating proprietary implementations of security features and services. [Formerly PW.4.3]
        PW.2: Review the Software Design to Verify Compliance with Security Requirements and Risk Information
            PW.2.1: Have 1) a qualified person (or people) who were not involved with the design and/or 2) automated processes instantiated in the toolchain review the software design to confirm and enforce that it meets all of the security requirements and satisfactorily addresses the identified risk information.
        PW.3: Verify Third-Party Software Complies with Security Requirements: Moved to PW.4
            PW.3.1: Moved to PO.1.3
            PW.3.2: Moved to PW.4.4
        PW.4: Reuse Existing, Well-Secured Software When Feasible Instead of Duplicating Functionality
            PW.4.1: Acquire and maintain well-secured software components (e.g., software libraries, modules, middleware, frameworks) from commercial, opensource, and other third-party developers for use by the organization’s software.
            PW.4.2: Create and maintain well-secured software components in-house following SDLC processes to meet common internal software development needs that cannot be better met by third-party software components.
            PW.4.3: Moved to PW.1.3
            PW.4.4: Verify that acquired commercial, open-source, and all other third-party software components comply with the requirements, as defined by the organization, throughout their life cycles.
            PW.4.5: Moved to PW.4.1 and PW.4.4
        PW.5: Create Source Code by Adhering to Secure Coding Practices
            PW.5.1: Follow all secure coding practices that are appropriate to the development languages and environment to meet the organization’s requirements.
            PW.5.2: Moved to PW.5.1 as example
        PW.6: Configure the Compilation, Interpreter, and Build Processes to Improve Executable Security
            PW.6.1: Use compiler, interpreter, and build tools that offer features to improve executable security
            PW.6.2: Determine which compiler, interpreter, and build tool features should be used and how each should be configured, then implement and use the approved configurations.
        PW.7: Review and/or Analyze Human-Readable Code to Identify Vulnerabilities and Verify Compliance with Security Requirements
            PW.7.1: Determine whether code review (a person looks directly at the code to find issues) and/or code analysis (tools are used to find issues in code, either in a fully automated way or in conjunction with a person) should be used, as defined by the organization.
            PW.7.2: Perform the code review and/or code analysis based on the organization’s secure coding standards, and record and triage all discovered issues and recommended remediations in the development team’s workflow or issue tracking system.
        PW.8: Test Executable Code to Identify Vulnerabilities and Verify Compliance with Security Requirements
            PW.8.1: Determine whether executable code testing should be performed to find vulnerabilities not identified by previous reviews, analysis, or testing and, if so, which types of testing should be used.
            PW.8.2: Scope the testing, design the tests, perform the testing, and document the results, including recording and triaging all discovered issues and recommended remediations in the development team’s workflow or issue tracking system.
        PW.9: Configure Software to Have Secure Settings by Default
            PW.9.1: Define a secure baseline by determining how to configure each setting that has an effect on security or a security-related setting so that the default settings are secure and do not weaken the security functions provided by the platform, network infrastructure, or services.
            PW.9.2: Implement the default settings (or groups of default settings, if applicable), and document each setting for software administrators.
    PV(Respond to Vulnerabilities)
        RV.1: Identify and Confirm Vulnerabilities on an Ongoing Basis
            RV.1.1: Gather information from software acquirers, users, and public sources on potential vulnerabilities in the software and third-party components that the software uses, and investigate all credible reports.
            RV.1.2: Review, analyze, and/or test the software’s code to identify or confirm the presence of previously undetected vulnerabilities.
            RV.1.3: Have a policy that addresses vulnerability disclosure and remediation, and implement the roles, responsibilities, and processes needed to support that policy.
        RV.2: Assess, Prioritize, and Remediate Vulnerabilities
            RV.2.1: Analyze each vulnerability to gather sufficient information about risk to plan its remediation or other risk response.
            RV.2.2: Plan and implement risk responses for vulnerabilities.
        RV.3: Analyze Vulnerabilities to Identify Their Root Causes
            RV.3.1: Analyze identified vulnerabilities to determine their root causes.
            RV.3.2: Analyze the root causes over time to identify patterns, such as a particular secure coding practice not being followed consistently.
            RV.3.3: Review the software for similar vulnerabilities to eradicate a class of vulnerabilities, and proactively fix them rather than waiting for external reports.
            RV.3.4: Review the SDLC process, and update it if appropriate to prevent (or reduce the likelihood of) the root cause recurring in updates to the software or in new software that is created.

SAMM v2
https://owaspsamm.org/release-notes-v2/
    Stream A
        Governance
            Strategy and Metrics
                Maturity level 1: Identify objectives and means of measuring effectiveness of the security program.
                    Stream A: Create and Promote
                        Identify organization drivers as they relate to the organization's risk tolerance.
                Maturity level 2: Establish a unified strategic roadmap for software security within the organization.
                    Stream A: Create and Promote
                        Publish a unified strategy for application security.
                Maturity level 3: Align security efforts with the relevant organizational indicators and asset values.
                    Stream A: Create and Promote
                        Align the application security program to support the organization's growth.
            Policy and Compliance
                Maturity level 1: Identify and document governance and compliance drivers relevant to the organization.
                    Stream A: Policy and Standards
                        Determine a security baseline representing organization's policies and standards.
                Maturity level 2: Establish application-specific security and compliance baseline.
                    Stream A: Policy and Standards
                        Develop security requirements applicable to all applications.
                Maturity level 3: Measure adherence to policies, standards, and 3rd-party requirements.
                    Stream A: Policy and Standards
                        Measure and report on the status of individual application's adherence to policies and standards.
            Education and Guidance
                Maturity level 1: Offer staff access to resources around the topics of secure development and deployment.
                    Stream A: Training and Awareness
                        Provide security awareness training for all personnel involved in software development.
                Maturity level 2: Educate all personnel in the software lifecycle with technology and role-specific guidance on secure development.
                    Stream A: Training and Awareness
                        Offer technology and role-specific guidance, including security nuances of each language and platform.
                Maturity level 3: Develop in-house training programs facilitated by developers across different teams.
                    Stream A: Training and Awareness
                        Standardized in-house guidance around the organization's secure software development standards.
        Design
            Threat Assessment
                Maturity level 1: Best-effort identification of high-level threats to the organization and individual projects.
                    Stream A: Application Risk Profile
                        A basic assessment of the application risk is performed to understand likelihood and impact of an attack.
                Maturity level 2: Standardization and enterprise-wide analysis of software-related threats within the organization.
                    Stream A: Application Risk Profile
                        Understand the risk for all applications in the organization by centralizing the risk profile inventory for stakeholders.
                Maturity level 3: Proactive improvement of threat coverage throughout the organization.
                    Stream A: Application Risk Profile
                        Periodically review application risk profiles at regular intervals to ensure accuracy and reflect current state.
            Security Requirements
                Maturity level 1: Consider security explicitly during the software requirements process.
                    Stream A: Software Requirements
                        High-level application security objectives are mapped to functional requirements.
                Maturity level 2: Increase granularity of security requirements derived from business logic and known risks.
                    Stream A: Software Requirements
                        Structured security requirements are available and utilized by developer teams.
                Maturity level 3: Mandate security requirements process for all software projects and third-party dependencies.
                    Stream A: Software Requirements
                        Build a requirements framework for product teams to utilize.
            Secure Architecture
                Maturity level 1: Insert consideration of proactive security guidance into the software design process.
                    Stream A: Architecture Design
                        Teams are trained on the use of basic security principles during design.
                Maturity level 2: Direct the software design process toward known secure services and secure-by-default designs.
                    Stream A: Architecture Design
                        Establish common design patterns and security solutions for adoption.
                Maturity level 3: Formally control the software design process and validate utilization of secure components.
                    Stream A: Architecture Design
                        Reference architectures are utilized and continuously evaluated for adoption and appropriateness.
        Implementation
            Secure Build
                Maturity level 1: Build process is repeatable and consistent.
                    Stream A: Build Process
                        Create a formal definition of the build process so that it becomes consistent and repeatable.
                Maturity level 2: Build process is optimized and fully integrated into the workflow.
                    Stream A: Build Process
                        Automate your build pipeline and secure the used tooling. Add security checks in the build pipeline.
                Maturity level 3: Build process helps prevent known defects from entering the production environment.
                    Stream A: Build Process
                        Define mandatory security checks in the build process and ensure that building non-compliant artifacts fails.
            Secure Deployment
                Maturity level 1: Deployment processes are fully documented.
                    Stream A: Deployment Process
                        Formalize the deployment process and secure the used tooling and processes.
                Maturity level 2: Deployment processes include security verification milestones.
                    Stream A: Deployment Process
                        Automate the deployment process over all stages and introduce sensible security verification tests.
                Maturity level 3: Deployment process is fully automated and incorporates automated verification of all critical milestones.
                    Stream A: Deployment Process
                        Automatically verify integrity of all deployed software, independently on whether it's internally or externally developed.
            Defect Management
                Maturity level 1: All defects are tracked within each project.
                    Stream A: Defect Tracking
                        Introduce a structured tracking of security defects and make knowledgeable decisions based on this information.
                Maturity level 2: Defect tracking used to influence the deployment process.
                    Stream A: Defect Tracking
                        Rate all security defects over the whole organization consistently and define SLAs for particular severity classes.
                Maturity level 3: Defect tracking across multiple components is used to help reduce the number of new defects.
                    Stream A: Defect Tracking
                        Enforce the predefined SLAs and integrate your defect management system with other relevant tooling.
        Verification
            Architecture Assessment
                Maturity level 1: Review the architecture to ensure baseline mitigations are in place for typical risks.
                    Stream A: Architecture Validation
                        Identify application and infrastructure architecture components and review for basic security provisioning.
                Maturity level 2: Review the complete provision of security mechanisms in the architecture.
                    Stream A: Architecture Validation
                        Validate the architecture security mechanisms.
                Maturity level 3: Review the architecture effectiveness and feedback results to improve the security of the architecture.
                    Stream A: Architecture Validation
                        Review of the architecture components' effectiveness.
            Requirements-driven Testing
                Maturity level 1: Opportunistically find basic vulnerabilities and other security issues.
                    Stream A: Control Verification
                        Test for software security controls.
                Maturity level 2: Perform implementation review to discover application-specific risks against the security requirements.
                    Stream A: Control Verification
                        Derive test cases from known security requirements.
                Maturity level 3: Maintain the application security level after bug fixes, changes or during maintenance.
                    Stream A: Control Verification
                        Perform regression testing (with security unit tests).
            Security Testing
                Maturity level 1: Perform security testing (both manual and tool based) to discover security defects.
                    Stream A: Scalable Baseline
                        Utilize automated security testing tools.
                Maturity level 2: Make security testing during development more complete and efficient through automation complemented with regular manual security penetration tests.
                    Stream A: Scalable Baseline
                        Employ application-specific security testing automation.
                Maturity level 3: Embed security testing as part of the development and deployment processes.
                    Stream A: Scalable Baseline
                        Integrate automated security testing into the build and deploy process.
        Operations
            Incident Management
                Maturity level 1: Best-effort incident detection and handling
                    Stream A: Incident Detection
                        Use available log data to perform best-effort detection of possible security incidents.
                Maturity level 2: Formal incident management process in place
                    Stream A: Incident Detection
                        Follow an established, well-documented process for incident detection, with emphasis on automated log evaluation.
                Maturity level 3: Mature incident management
                    Stream A: Incident Detection
                        Use a proactively managed process for detection of incidents.
            Environment Management
                Maturity level 1: Best-effort patching and hardening
                    Stream A: Configuration Hardening
                        Perform best-effort hardening of configurations, based on readily available information.
                Maturity level 2: Formal process with baselines in place
                    Stream A: Configuration Hardening
                        Perform consistent hardening of configurations, following established baselines and guidance.
                Maturity level 3: Conformity with continuously improving process enforced
                    Stream A: Configuration Hardening
                        Actively monitor configurations for non-conformance to baselines, and handle detected occurrences as security defects.
            Operational Management
                Maturity level 1: Foundational Practices
                    Stream A: Data Protection
                        Implement basic data protection practices.
                Maturity level 2: Managed, Responsive Processes
                    Stream A: Data Protection
                        Develop data catalog and establish data protection policy.
                Maturity level 3: Active Monitoring and Response
                    Stream A: Data Protection
                        Automate detection of policy non-compliance, and audit compliance periodically. Regularly review and update to data catalog and data protection policy.
    Stream B
        Governance
            Strategy and Metrics
                Maturity level 1: Identify objectives and means of measuring effectiveness of the security program.
                    Stream B: Measure and Improve
                        Define metrics with insight into the effectiveness and efficiency of the Application Security Program.
                Maturity level 2: Establish a unified strategic roadmap for software security within the organization.
                    Stream B: Measure and Improve
                        Set targets and KPI's for measuring the program effectiveness.
                Maturity level 3: Align security efforts with the relevant organizational indicators and asset values.
                    Stream B: Measure and Improve
                        Influence the strategy based on the metrics and organizational needs.
            Policy and Compliance
                Maturity level 1: Identify and document governance and compliance drivers relevant to the organization.
                    Stream B: Compliance Management
                        Identify 3rd-party compliance drivers and requirements and map to existing policies and standards.
                Maturity level 2: Establish application-specific security and compliance baseline.
                    Stream B: Compliance Management
                        Publish compliance-specific application requirements and test guidance.
                Maturity level 3: Measure adherence to policies, standards, and 3rd-party requirements.
                    Stream B: Compliance Management
                        Measure and report on individual application's compliance with 3rd party requirements.
            Education and Guidance
                Maturity level 1: Offer staff access to resources around the topics of secure development and deployment.
                    Stream B: Organization and Culture
                        Identify a "Security Champion" within each development team.
                Maturity level 2: Educate all personnel in the software lifecycle with technology and role-specific guidance on secure development.
                    Stream B: Organization and Culture
                        Develop a secure software center of excellence promoting thought leadership among developers and architects.
                Maturity level 3: Develop in-house training programs facilitated by developers across different teams.
                    Stream B: Organization and Culture
                        Build a secure software community including all organization people involved in software security.
        Design
            Threat Assessment
                Maturity level 1: Best-effort identification of high-level threats to the organization and individual projects.
                    Stream B: Threat Modeling
                        Perform best-effort, risk-based threat modeling using brainstorming and existing diagrams with simple threat checklists.
                Maturity level 2: Standardization and enterprise-wide analysis of software-related threats within the organization.
                    Stream B: Threat Modeling
                        Standardize threat modeling training, processes, and tools to scale across the organization.
                Maturity level 3: Proactive improvement of threat coverage throughout the organization.
                    Stream B: Threat Modeling
                        Continuously optimization and automation of your threat modeling methodology.
            Security Requirements
                Maturity level 1: Consider security explicitly during the software requirements process.
                    Stream B: Supplier Security
                        Evaluate the supplier based on organizational security requirements.
                Maturity level 2: Increase granularity of security requirements derived from business logic and known risks.
                    Stream B: Supplier Security
                        Build security into supplier agreements in order to ensure compliance with organizational requirements.
                Maturity level 3: Mandate security requirements process for all software projects and third-party dependencies.
                    Stream B: Supplier Security
                        Ensure proper security coverage for external suppliers by providing clear objectives.
            Secure Architecture
                Maturity level 1: Insert consideration of proactive security guidance into the software design process.
                    Stream B: Technology Management
                        Elicit technologies, frameworks and integrations within the overall solution to identify risk.
                Maturity level 2: Direct the software design process toward known secure services and secure-by-default designs.
                    Stream B: Technology Management
                        Standardize technologies and frameworks to be used throughout the different applications.
                Maturity level 3: Formally control the software design process and validate utilization of secure components.
                    Stream B: Technology Management
                        Impose the use of standard technologies on all software development.
        Implementation
            Secure Build
                Maturity level 1: Build process is repeatable and consistent.
                    Stream B: Software Dependencies
                        Create records with Bill of Materials of your applications and opportunistically analyze these.
                Maturity level 2: Build process is optimized and fully integrated into the workflow.
                    Stream B: Software Dependencies
                        Evaluate used dependencies and ensure timely reaction to situations posing risk to your applications.
                Maturity level 3: Build process helps prevent known defects from entering the production environment.
                    Stream B: Software Dependencies
                        Analyze used dependencies for security issues in a comparable way to your own code.
            Secure Deployment
                Maturity level 1: Deployment processes are fully documented.
                    Stream B: Secret Management
                        Introduce basic protection measures to limit access to your production secrets.
                Maturity level 2: Deployment processes include security verification milestones.
                    Stream B: Secret Management
                        Inject secrets dynamically during deployment process from hardened storages and audit all human access to them.
                Maturity level 3: Deployment process is fully automated and incorporates automated verification of all critical milestones.
                    Stream B: Secret Management
                        Improve the lifecycle of application secrets by regularly generating them and by ensuring proper use.
            Defect Management
                Maturity level 1: All defects are tracked within each project.
                    Stream B: Metrics and Feedback
                        Regularly go over previously recorded security defects and derive quick wins from basic metrics.
                Maturity level 2: Defect tracking used to influence the deployment process.
                    Stream B: Metrics and Feedback
                        Collect standardized defect management metrics and use these also for prioritization of centrally driven initiatives.
                Maturity level 3: Defect tracking across multiple components is used to help reduce the number of new defects.
                    Stream B: Metrics and Feedback
                        Continuously improve your security defect management metrics and correlate it with other sources.
        Verification
            Architecture Assessment
                Maturity level 1: Review the architecture to ensure baseline mitigations are in place for typical risks.
                    Stream B: Architecture Mitigation
                        Ad-hoc review of the architecture for unmitigated security threats.
                Maturity level 2: Review the complete provision of security mechanisms in the architecture.
                    Stream B: Architecture Mitigation
                        Analyze the architecture for known threats.
                Maturity level 3: Review the architecture effectiveness and feedback results to improve the security of the architecture.
                    Stream B: Architecture Mitigation
                        Feed the architecture review results back into the enterprise architecture, organization design principles and patterns, security solutions and reference architectures.
            Requirements-driven Testing
                Maturity level 1: Opportunistically find basic vulnerabilities and other security issues.
                    Stream B: Misuse/Abuse Testing
                        Perform security fuzzing testing.
                Maturity level 2: Perform implementation review to discover application-specific risks against the security requirements.
                    Stream B: Misuse/Abuse Testing
                        Create and test abuse cases and business logic flaw test.
                Maturity level 3: Maintain the application security level after bug fixes, changes or during maintenance.
                    Stream B: Misuse/Abuse Testing
                        Denial of service and security stress testing.
            Security Testing
                Maturity level 1: Perform security testing (both manual and tool based) to discover security defects.
                    Stream B: Deep Understanding
                        Perform manual security testing of high-risk components.
                Maturity level 2: Make security testing during development more complete and efficient through automation complemented with regular manual security penetration tests.
                    Stream B: Deep Understanding
                        Conduct manual penetration testing.
                Maturity level 3: Embed security testing as part of the development and deployment processes.
                    Stream B: Deep Understanding
                        Integrate security testing into development process.
        Operations
            Incident Management
                Maturity level 1: Best-effort incident detection and handling
                    Stream B: Incident Response
                        Identify roles and responsibilities for incident response.
                Maturity level 2: Formal incident management process in place
                    Stream B: Incident Response
                        Establish a formal incident response process and ensure staff are properly trained in performing their roles.
                Maturity level 3: Mature incident management
                    Stream B: Incident Response
                        Employ a dedicated, well-trained incident response team.
            Environment Management
                Maturity level 1: Best-effort patching and hardening
                    Stream B: Patching and Updating
                        Perform best-effort patching of system and application components.
                Maturity level 2: Formal process with baselines in place
                    Stream B: Patching and Updating
                        Perform regular patching of system and application components, across the full stack. Ensure timely delivery of patches to customers.
                Maturity level 3: Conformity with continuously improving process enforced
                    Stream B: Patching and Updating
                        Actively monitor update status and manage missing patches as security defects. Proactively obtain vulnerability and update information for components.
            Operational Management
                Maturity level 1: Foundational Practices
                    Stream B: System Decommissioning / Legacy Management
                        Decommission unused applications and services as identified. Manage customer upgrades/migrations individually.
                Maturity level 2: Managed, Responsive Processes
                    Stream B: System Decommissioning / Legacy Management
                        Develop repeatable decommissioning processes for unused systems/services, and for migration from legacy dependencies. Manage legacy migration roadmaps for customers.
                Maturity level 3: Active Monitoring and Response
                    Stream B: System Decommissioning / Legacy Management
                        Proactively manage migration roadmaps, for both unsupported end-of-life dependencies, and legacy versions of delivered software.

BSIMM 15
https://www.blackduck.com/resources/analyst-reports/bsimm.html?cmp=pr-sig&utm_medium=referral
    GOVERNANCE
        STRATEGY & METRICS
            [SM1.1] Publish process and evolve as necessary.
            [SM1.3] Educate executives on software security.
            [SM1.4] Implement security checkpoints and associated governance.
            [SM1.7] Enforce security checkpoints and track exceptions.
            [SM2.1] Publish data about software security internally and use it to drive change.
            [SM2.3] Create or grow a security champions program.
            [SM2.6] Require security sign-off prior to software release.
            [SM2.7] Create evangelism role and perform internal marketing.
            [SM3.1] Use a software asset tracking application with portfolio view.
            [SM3.2] Make SSI efforts part of external marketing.
            [SM3.3] Identify metrics and use them to drive resourcing.
            [SM3.4] Integrate software-defined lifecycle governance.
            [SM3.5] Integrate software supply chain risk management.
        COMPLIANCE & POLICY
            [CP1.1] Unify regulatory pressures.
            [CP1.2] Identify privacy obligations.
            [CP1.3] Create policy.
            [CP2.1] Build a PII inventory.
            [CP2.2] Require security sign-off for compliance-related risk.
            [CP2.3] Implement and track controls for compliance.
            [CP2.4] Include software security SLAs in all vendor contracts.
            [CP2.5] Ensure executive awareness of compliance and privacy obligations.
            [CP3.1] Document a software compliance story.
            [CP3.2] Ensure compatible vendor policies.
            [CP3.3] Drive feedback from software lifecycle data back to policy.
        TRAINING
            [T1.1] Conduct software security awareness training.
            [T1.7] Deliver on-demand individual training.
            [T1.8] Include security resources in onboarding.
            [T2.5] Enhance security champions through training and events.
            [T2.8] Create and use material specific to company history.
            [T2.9] Deliver role-specific advanced curriculum.
            [T2.10] Host software security events.
            [T2.11] Require an annual refresher.
            [T2.12] Provide expertise via open collaboration channels.
            [T3.1] Reward progression through curriculum.
            [T3.2] Provide training for vendors and outsourced workers.
            [T3.6] Identify new security champions through observation.
    INTELLIGENCE
        ATTACK MODELS
            [AM1.2] Use a data classification scheme for software inventory.
            [AM1.3] Identify potential attackers.
            [AM1.5] Gather and use attack intelligence.
            [AM2.1] Build attack patterns and abuse cases tied to potential attackers.
            [AM2.6] Collect and publish attack stories.
            [AM2.7] Build an internal forum to discuss attacks.
            [AM2.8] Have a research group that develops new attack methods.
            [AM2.9] Monitor automated asset creation.
            [AM3.2] Create and use automation to mimic attackers.
            [AM3.4] Create technology-specific attack patterns.
            [AM3.5] Maintain and use a top N possible attacks list.
        SECURITY FEATURES & DESIGN
            [SFD1.1] Integrate and deliver security features.
            [SFD1.2] Application architecture teams engage with the SSG.
            [SFD2.1] Leverage secure-by-design components and services.
            [SFD2.2] Create capability to solve difficult design problems.
            [SFD3.1] Form a review board to approve and maintain secure design patterns.
            [SFD3.2] Require use of approved security features and frameworks.
            [SFD3.3] Find and publish secure design patterns from the organization.
        STANDARDS & REQUIREMENTS
            [SR1.1] Create security standards.
            [SR1.2] Create a security portal.
            [SR1.3] Translate compliance constraints to requirements.
            [SR1.5] Identify open source.
            [SR2.2] Create a standards review process.
            [SR2.5] Create SLA boilerplate.
            [SR2.7] Control open source risk.
            [SR3.2] Communicate standards to vendors.
            [SR3.3] Use secure coding standards.
            [SR3.4] Create standards for technology stacks.
            [SR3.5] Create standards controlling and guiding the adoption of new technologies.
    SSDL TOUCHPOINTS
        ARCHITECTURE ANALYSIS
            [AA1.1] Perform security feature review.
            [AA1.2] Perform design review for high-risk applications.
            [AA1.4] Use a risk methodology to rank applications.
            [AA2.1] Perform architecture analysis using a defined process.
            [AA2.2] Standardize architectural descriptions.
            [AA2.4] Have SSG lead design review efforts.
            [AA3.1] Have engineering teams lead AA process.
            [AA3.2] Drive analysis results into standard design patterns.
            [AA3.3] Make the SSG available as an AA resource or mentor.
        CODE REVIEW
            [CR1.2] Perform opportunistic code review.
            [CR1.4] Use automated code review tools.
            [CR1.5] Make code review mandatory for all projects.
            [CR1.7] Assign code review tool mentors.
            [CR2.6] Use custom rules with automated code review tools.
            [CR2.7] Use a top N bugs list (real data preferred).
            [CR2.8] Use centralized defect reporting to close the knowledge loop.
            [CR3.2] Build a capability to combine AST results.
            [CR3.3] Create capability to eradicate bugs.
            [CR3.4] Automate malicious code detection.
            [CR3.5] Enforce secure coding standards.
        SECURITY TESTING
            [ST1.1] Perform edge/boundary value condition testing during QA.
            [ST1.3] Drive tests with security requirements and security features.
            [ST1.4] Integrate opaque-box security tools into the QA process.
            [ST2.4] Drive QA tests with AST results.
            [ST2.5] Include security tests in QA automation.
            [ST2.6] Perform fuzz testing customized to application APIs.
            [ST3.3] Drive tests with design review results.
            [ST3.4] Leverage code coverage analysis.
            [ST3.5] Begin to build and apply adversarial security tests (abuse cases).
            [ST3.6] Implement event-driven security testing in automation.
    DEPLOYMENT
        PENETRATION TESTING
            [PT1.1] Use external penetration testers to find problems.
            [PT1.2] Feed results to the defect management and mitigation system.
            [PT1.3] Use penetration testing tools internally.
            [PT2.2] Penetration testers use all available information.
            [PT2.3] Schedule periodic penetration tests for application coverage.
            [PT3.1] Use external penetration testers to perform deep-dive analysis.
            [PT3.2] Customize penetration testing tools.
        SOFTWARE ENVIRONMENT
            [SE1.1] Use application input monitoring for security purposes.
            [SE1.2] Ensure host and network security basics are in place.
            [SE1.3] Implement cloud security controls.
            [SE1.4] Define secure deployment parameters and configurations.
            [SE2.4] Protect code integrity.
            [SE2.5] Use application containers to support security goals.
            [SE2.7] Use orchestration for containers and virtualized environments.
            [SE3.2] Use code protection.
            [SE3.3] Use application behavior monitoring and diagnostics.
            [SE3.6] Create bills of materials for deployed software.
            [SE3.8] Perform application composition analysis on code repositories.
            [SE3.9] Protect integrity of development toolchains.
            [SE3.10] Protect the integrity of development endpoints.
        CONFIGURATION MANAGEMENT & VULNERABILITY MANAGEMENT
            [CMVM1.1] Create or interface with incident response.
            [CMVM1.2] Identify software defects found in operations monitoring and feed them back to engineering.
            [CMVM1.3] Track software defects found in operations through the fix process.
            [CMVM1.4] Have emergency response.
            [CMVM2.3] Develop an operations software inventory.
            [CMVM2.4] Streamline incoming responsible vulnerability disclosure.
            [CMVM3.1] Fix all occurrences of software defects found in operations.
            [CMVM3.2] Enhance the SSDL to prevent software defects found in operations.
            [CMVM3.3] Simulate software crises.
            [CMVM3.4] Operate a bug bounty program.
            [CMVM3.5] Automate verification of operational infrastructure security.
            [CMVM3.6] Publish risk data for deployable artifacts.
            [CMVM3.8] Do attack surface management for deployed applications.

DSOMM
https://dsomm.owasp.org/
    Build and Deployment
        Build
            Level 1: Basic understanding of security practices
                Defined build process
            Level 2: Adoption of basic security practices
                Building and testing of artifacts in virtual environments
                Pinning of artifacts
                SBOM of components
            Level 3: High adoption of security practices
                Signing of code
            Level 4: Very high adoption of security practices
            Level 5: Advanced deployment of security practices at scale
                Signing of artifacts
        Deployment
            Level 1: Basic understanding of security practices
                Defined deployment process
                Inventory of production components
            Level 2: Adoption of basic security practices
                Defined decommissioning process
                Environment depending configuration parameters (secrets)
                Evaluation of the trust of used components
                Inventory of production artifacts
            Level 3: High adoption of security practices
                Handover of confidential parameters
                Inventory of production dependencies
                Rolling update on deployment
            Level 4: Very high adoption of security practices
                Same artifact for environments
                Usage of feature toggles
            Level 5: Advanced deployment of security practices at scale
                Blue/Green Deployment
        Patch Management
            Level 1: Basic understanding of security practices
                A patch policy is defined
                Automated PRs for patches
            Level 2: Adoption of basic security practices
                Automated merge of automated PRs
                Nightly build of images (base images)
                Reduction of the attack surface
                Usage of a maximum lifetime for images
            Level 3: High adoption of security practices
                Automated deployment of automated PRs
            Level 4: Very high adoption of security practices
                Usage of a short maximum lifetime for images
            Level 5: Advanced deployment of security practices at scale
    Culture and Organization
        Design
            Level 1: Basic understanding of security practices
                Conduction of simple threat modeling on technical level
            Level 2: Adoption of basic security practices
                Information security targets are communicated
            Level 3: High adoption of security practices
                Conduction of simple threat modeling on business level
                Creation of simple abuse stories
                Creation of threat modeling processes and standards
            Level 4: Very high adoption of security practices
                Conduction of advanced threat modeling
            Level 5: Advanced deployment of security practices at scale
                Creation of advanced abuse stories
        Education and Guidance
            Level 1: Basic understanding of security practices
                Ad-Hoc Security trainings for software developers
                Security consulting on request
            Level 2: Adoption of basic security practices
                Each team has a security champion
                Regular security training for all
                Regular security training of security champions
                Reward of good communication
                Security code review
            Level 3: High adoption of security practices
            Conduction of build-it, break-it, fix-it contests
                Office Hours
                Security Coaching
                Security-Lessoned-Learned
                Simple mob hacking
            Level 4: Very high adoption of security practices
                Aligning security in teams
                Conduction of collaborative team security checks
                Conduction of war games
                Regular security training for externals
            Level 5: Advanced deployment of security practices at scale
                Conduction of collaborative security checks with developers and system administrators
        Process
            Level 1: Basic understanding of security practices
                Definition of simple BCDR practices for critical components
            Level 2: Adoption of basic security practices
                Determining the protection requirement
            Level 3: High adoption of security practices
                Approval by reviewing any new version
                Definition of a change management process
            Level 4: Very high adoption of security practices
            Level 5: Advanced deployment of security practices at scale
    Implementation
        Application Hardening
            Level 1: Basic understanding of security practices
                App. Hardening Level 1 (50%)
                Contextualized Encoding
            Level 2: Adoption of basic security practices
                App. Hardening Level 1
            Level 3: High adoption of security practices
                App. Hardening Level 2 (75%)
            Level 4: Very high adoption of security practices
                App. Hardening Level 2
            Level 5: Advanced deployment of security practices at scale
                App. Hardening Level 3
        Development and Source Control
            Level 1: Basic understanding of security practices
                Versioning
            Level 2: Adoption of basic security practices
                Require a PR before merging
            Level 3: High adoption of security practices
                Block force pushes
                Dismiss stale PR approvals
                Require status checks to pass
            Level 4: Very high adoption of security practices
                .gitignore
            Level 5: Advanced deployment of security practices at scale
                Local development linting & style checks performed
        Infrastructure Hardening
            Level 1: Basic understanding of security practices
                MFA for admins
                Simple access control for systems
                Usage of edge encryption at transit
            Level 2: Adoption of basic security practices
                Applications are running in virtualized environments
                Backup
                Baseline Hardening of the environment
                Isolated networks for virtual environments
                MFA
                Usage of an security account
                Usage of encryption at rest
                Usage of test and production environments
                Virtual environments are limited
            Level 3: High adoption of security practices
                Filter outgoing traffic
                Immutable infrastructure
                Infrastructure as Code
                Limitation of system events
                Role based authentication and authorization
                Usage of internal encryption at transit
                Usage of security by default for components
                WAF baseline
            Level 4: Very high adoption of security practices
                Hardening of the Environment
                Production near environments are used by developers
                Usage of a chaos monkey
                WAF medium
            Level 5: Advanced deployment of security practices at scale
                Microservice-architecture
                WAF Advanced
    Information Gathering
        Logging
            Level 1: Basic understanding of security practices
                Centralized system logging
            Level 2: Adoption of basic security practices
                Logging of security events
                Visualized logging
            Level 3: High adoption of security practices
                Centralized application logging
            Level 4: Very high adoption of security practices
            Level 5: Advanced deployment of security practices at scale
                Correlation of security events
                PII logging concept
        Monitoring
            Level 1: Basic understanding of security practices
                Simple application metrics
                Simple budget metrics
                Simple system metrics
            Level 2: Adoption of basic security practices
                Alerting
                Monitoring of costs
                Visualized metrics
            Level 3: High adoption of security practices
                Advanced availability and stability metrics
                Audit of system events
                Deactivation of unused metrics
                Grouping of metrics
                Targeted alerting
            Level 4: Very high adoption of security practices
                Advanced app. metrics
                Coverage and control metrics
                Defense metrics
                Screens with metric visualization
            Level 5: Advanced deployment of security practices at scale
                Metrics are combined with tests
        Test KPI
            Level 1: Basic understanding of security practices
            Level 2: Adoption of basic security practices
                Number of vulnerabilities/severity
                Number of vulnerabilities/severity/layer
                Patching mean time to resolution via PR
            Level 3: High adoption of security practices
                Fix rate per repo/product
                Generation of response statistics
                SLA per criticality
            Level 4: Very high adoption of security practices
                Patching mean time to resolution via production
            Level 5: Advanced deployment of security practices at scale
    Test and Verification
        Application tests
            Level 1: Basic understanding of security practices
            Level 2: Adoption of basic security practices
                Security unit tests for important components
            Level 3: High adoption of security practices
                Security integration tests for important components
            Level 4: Very high adoption of security practices
                Smoke Test
            Level 5: Advanced deployment of security practices at scale
                High coverage of security related module and integration tests
        Consolidation
            Level 1: Basic understanding of security practices
                Fix based on severity
                Simple false positive treatment
                Treatment of defects with severity high or higher
            Level 2: Adoption of basic security practices
                Simple visualization of defects
            Level 3: High adoption of security practices
                Fix based on accessibility
                Integration in development process
                Integration of vulnerability issues into the development process
                Treatment of defects per protection requirement
                Treatment of defects with severity middle
                Usage of a vulnerability management system
            Level 4: Very high adoption of security practices
                Advanced visualization of defects
                Reproducible defect tickets
            Level 5: Advanced deployment of security practices at scale
                Treatment of all defects
        Dynamic depth for applications
            Level 1: Basic understanding of security practices
            Level 2: Adoption of basic security practices
                Coverage of client side dynamic components
                Simple Scan
                Usage of different roles
            Level 3: High adoption of security practices
                Coverage of hidden endpoints
                Coverage of more input vectors
                Coverage of sequential operations
            Level 4: Very high adoption of security practices
                Usage of multiple scanners
            Level 5: Advanced deployment of security practices at scale
                Coverage analysis
                Coverage of service to service communication
        Dynamic depth for infrastructure
            Level 1: Basic understanding of security practices
            Level 2: Adoption of basic security practices
                Test for exposed services
                Test network segmentation
                Test of the configuration of cloud environments
            Level 3: High adoption of security practices
                Test for unauthorized installation
                Weak password test
            Level 4: Very high adoption of security practices
                Load tests
            Level 5: Advanced deployment of security practices at scale
                Test for unused Resources
        Static depth for applications
            Level 1: Basic understanding of security practices
            Level 2: Adoption of basic security practices
                Software Composition Analysis (server side)
                Test for Time to Patch
                Test libyear
            Level 3: High adoption of security practices
                API design validation
                Exploit likelihood estimation
                Local development security checks performed
                Software Composition Analysis (client side)
                Static analysis for important client side components
                Static analysis for important server side components
                Test for Patch Deployment Time
            Level 4: Very high adoption of security practices
                Static analysis for all self written components
                Usage of multiple analyzers
            Level 5: Advanced deployment of security practices at scale
                Dead code elimination
                Exclusion of source code duplicates
                Static analysis for all components/libraries
                Stylistic analysis
        Static depth for infrastructure
            Level 1: Basic understanding of security practices
                Test for stored secrets
            Level 2: Adoption of basic security practices
                Test cluster deployment resources
                Test for image lifetime
                Test of virtualized environments
                Test the cloud configuration
                Test the definition of virtualized environments
            Level 3: High adoption of security practices
                Analyze logs
                Test for malware
                Test for new image version
            Level 4: Very high adoption of security practices
                Correlate known vulnerabilities in infrastructure with new image versions
                Software Composition Analysis
                Test of infrastructure components for known vulnerabilities
            Level 5: Advanced deployment of security practices at scale
        Test-Intensity
            Level 1: Basic understanding of security practices
                Default settings for intensity
                High test intensity
            Level 2: Adoption of basic security practices
                Regular automated tests
            Level 3: High adoption of security practices
                Deactivating of unneeded tests
            Level 4: Very high adoption of security practices
                Creation and application of a testing concept
            Level 5: Advanced deployment of security practices at scale

CMMC
https://dodcio.defense.gov/cmmc/About/
    Level1. Foundational: 14 based on FAR 52.204-21 cross referenced to NIST SP 800-171 rev 2
    Level2. Advanced: 110 practices aligned with NIST SP 800-171
    Level3. Expert: 110+ practices based on NIST SP 800-171 plus a subset of the security requirements in NIST SP 800-172