```julia
init_model!(
    model::EasyABM.GraphModel;
    initialiser,
    props_to_record
)

```

Initiates the simulation with a user defined initialiser function which takes the model as its only argument.  Model properties along with agent and graph properties can be set (or modified) from within a user defined function and then sending  it as `initialiser` argument in `init_model!`. The properties of  agents, nodes, edges and the model that are to be recorded during time evolution can be specified through the dictionary argument `props_to_record`.  List of agent properties to be recorded are specified with key "agents" and value the set of property names as symbols. If a nonempty set of  agents properties is specified, it will override the `keeps_record_of` property of each agent. Properties of nodes, edges and model are similarly specified with keys "nodes", "edges" and "model" respectively.
