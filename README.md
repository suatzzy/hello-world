# hello-world
just a demo repository
i'm a pervert
flowchart TD
    subgraph cnn_cal ["cnn_cal"]
        subgraph MAC_Module ["MAC"]
            direction LR
            conv[conv] -.- relu[relu] -.- pool[pool]
        end
        fc_Module(["fc"])
    end

    L1_cache(["L1_cache (Cache Layer)"])

    %% MAC 与 L1_cache 的交互
    L1_cache -- "RGB dequant data" --> MAC_Module
    MAC_Module -- "pooling1_data" --> L1_cache
    L1_cache -- "pooling1_ram_rdata" --> MAC_Module
    MAC_Module -- "pooling2_data" --> L1_cache

    %% fc 与 L1_cache 的交互
    L1_cache -- "pooling2_ram_rdata" --> fc_Module
    fc_Module -- "fc1_data" --> L1_cache
    L1_cache -- "fc1_ram_rdata" --> fc_Module
    fc_Module -- "fc2_data" --> L1_cache
    L1_cache -- "fc2_ram_rdata" --> fc_Module
    fc_Module -- "fc3_data" --> L1_cache

    %% 样式美化
    style cnn_cal fill:#8BC34A,stroke:#333,stroke-width:2px,color:#000
    style MAC_Module fill:#009688,stroke:#333,stroke-width:2px,color:#000
    style conv fill:#D32F2F,color:#fff
    style relu fill:#D32F2F,color:#fff
    style pool fill:#D32F2F,color:#fff
    style fc_Module fill:#673AB7,stroke:#333,stroke-width:2px,color:#fff
    style L1_cache fill:#DCE775,stroke:#333,stroke-width:2px,stroke-dasharray: 5 5,color:#000
