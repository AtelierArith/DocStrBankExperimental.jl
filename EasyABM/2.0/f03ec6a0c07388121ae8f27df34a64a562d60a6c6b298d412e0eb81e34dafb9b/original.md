```julia
grid_2d_agent(
;
    pos,
    space_type,
    agent_type,
    kwargs...
) -> EasyABM.Agent2D{Int64, EasyABM.PeriodicType, EasyABM.StaticType}

```

Creates a single 2d agent with properties specified as keyword arguments.  Following property names are reserved for some specific agent properties      - pos : position     - vel : velocity     - shape : shape of agent     - color : color of agent     - size : size of agent     - orientation : orientation of agent     - `keeps_record_of` : Set of properties that the agent records during time evolution. 
