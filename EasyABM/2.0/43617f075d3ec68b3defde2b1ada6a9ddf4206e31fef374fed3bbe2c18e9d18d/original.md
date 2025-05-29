```julia
graph_agent(
;
    node,
    graph_mort_type,
    agent_type,
    kwargs...
) -> EasyABM.GraphAgent{EasyABM.StaticType, EasyABM.StaticType}

```

Creates a single graph agent with properties specified as keyword arguments. Following property names are reserved for some specific agent properties      - node : node where the agent is located on the graph.      - shape : shape of agent     - color : color of agent     - size : size of agent     - orientation : orientation of agent     - `keeps_record_of` : Set of properties that the agent records during time evolution. 
