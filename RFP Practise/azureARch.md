graph TB
    subgraph "Entry Point - Azure Front Services"
        AFD[☁️ Azure Front Door<br/>━━━━━━━━━━━━━━━<br/>• Global Load Balancer<br/>• SSL/TLS Termination<br/>• WAF Protection<br/>• DDoS Protection<br/>• URL Routing<br/>• Health Probes]
        
        CDN[🌍 Azure CDN<br/>━━━━━━━━━━━━━━━<br/>• Static Content<br/>• Image Optimization<br/>• Global Distribution<br/>• Cache Rules]
    end
    
    subgraph "API Gateway Layer"
        APIM[⚡ Azure API Management<br/>━━━━━━━━━━━━━━━<br/>Premium Tier<br/>• API Gateway<br/>• Rate Limiting<br/>• API Versioning<br/>• OAuth Integration<br/>• Developer Portal<br/>• Analytics]
    end
    
    subgraph "Identity & Security"
        AAD[🔐 Azure AD B2C<br/>━━━━━━━━━━━━━━━<br/>• Customer Identity<br/>• Social Login<br/>• MFA<br/>• Custom Policies]
        
        KV[🔑 Key Vault<br/>━━━━━━━━━━━━━━━<br/>Premium Tier<br/>• Secrets<br/>• Certificates<br/>• Keys<br/>• HSM Support]
    end
    
    subgraph "Compute - AKS Cluster"
        AKS[🐳 Azure Kubernetes Service<br/>━━━━━━━━━━━━━━━<br/>Standard Tier<br/>• 3-5 Node Pool<br/>• Auto-scaling<br/>• Pod Security<br/>• Helm Charts]
        
        ACR[📦 Container Registry<br/>━━━━━━━━━━━━━━━<br/>• Docker Images<br/>• Vulnerability Scan<br/>• Geo-replication]
    end
    
    subgraph "Data Tier - Azure SQL"
        SQL[💾 Azure SQL Database<br/>━━━━━━━━━━━━━━━<br/>Business Critical Tier<br/>• 4 vCores<br/>• Zone Redundant<br/>• Auto Backup<br/>• Point-in-time Restore<br/>• Read Scale-out]
        
        REDIS[⚡ Azure Cache for Redis<br/>━━━━━━━━━━━━━━━<br/>Premium Tier<br/>• 6GB Cache<br/>• Persistence<br/>• Clustering<br/>• Geo-replication]
        
        STORAGE[📁 Azure Storage Account<br/>━━━━━━━━━━━━━━━<br/>• Blob Storage (Hot)<br/>• File Share<br/>• Queue Storage<br/>• Encryption at Rest]
    end
    
    subgraph "Messaging & Events"
        SB[📨 Service Bus<br/>━━━━━━━━━━━━━━━<br/>Premium Tier<br/>• Queues<br/>• Topics/Subscriptions<br/>• Dead Letter<br/>• Duplicate Detection]
        
        EG[⚡ Event Grid<br/>━━━━━━━━━━━━━━━<br/>• Event Routing<br/>• Pub/Sub<br/>• Cloud Events]
    end
    
    subgraph "Integration Services"
        FUNC[⚙️ Azure Functions<br/>━━━━━━━━━━━━━━━<br/>Premium Plan<br/>• .NET 8 Isolated<br/>• Event Triggers<br/>• VNET Integration]
        
        LOGIC[🔄 Logic Apps<br/>━━━━━━━━━━━━━━━<br/>Standard Tier<br/>• Email Connector<br/>• SMS Connector<br/>• ERP Integration]
    end
    
    subgraph "Monitoring & DevOps"
        AI[📊 Application Insights<br/>━━━━━━━━━━━━━━━<br/>• APM<br/>• Live Metrics<br/>• Alerts<br/>• Distributed Tracing]
        
        LA[📋 Log Analytics<br/>━━━━━━━━━━━━━━━<br/>• KQL Queries<br/>• Workbooks<br/>• Dashboards]
        
        ADO[🚀 Azure DevOps<br/>━━━━━━━━━━━━━━━<br/>• Git Repos<br/>• CI/CD Pipelines<br/>• Artifacts<br/>• Test Plans]
    end
    
    AFD --> APIM
    AFD --> CDN
    APIM --> AAD
    APIM --> AKS
    
    AKS --> KV
    AKS --> SQL
    AKS --> REDIS
    AKS --> STORAGE
    AKS --> SB
    
    ACR --> AKS
    
    SB --> FUNC
    SB --> LOGIC
    EG --> FUNC
    
    AKS --> AI
    FUNC --> AI
    AI --> LA
    
    ADO -.->|Deploy| AKS
    ADO -.->|Build| ACR
    
    style AFD fill:#0078d4,stroke:#fff,stroke-width:2px,color:#fff
    style APIM fill:#ff6b00,stroke:#fff,stroke-width:2px,color:#fff
    style AAD fill:#00bcf2,stroke:#fff,stroke-width:2px,color:#fff
    style AKS fill:#326ce5,stroke:#fff,stroke-width:2px,color:#fff
    style SQL fill:#0078d4,stroke:#fff,stroke-width:2px,color:#fff
    style REDIS fill:#dc382d,stroke:#fff,stroke-width:2px,color:#fff
    style SB fill:#59b4d9,stroke:#fff,stroke-width:2px,color:#fff
    style AI fill:#68217a,stroke:#fff,stroke-width:2px,color:#fff
