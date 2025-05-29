```julia
init_model!(
    model::EasyABM.SpaceModel2D;
    initialiser,
    props_to_record
)

```

Initiates the simulation with a user defined initialiser function which takes the model as its only argument.  Model properties along with agent properties can be set (or modified) from within a user defined function and then sending it as `initialiser` argument in `init_model!`. The properties of  agents, patches and model that are to be recorded during time evolution can be specified through the dictionary argument `props_to_record`.  List of agent properties to be recorded are specified with key "agents" and value the list of property names as symbols. If a nonempty list of  agents properties is specified, it will replace the `keeps_record_of` list of each agent. Properties of patches and model are similarly specified with keys "patches" and "model" respectively.
