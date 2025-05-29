```
AgentBasedModel
```

`AgentBasedModel` is the abstract supertype encompassing models in Agents.jl. All models are some concrete implementation of `AgentBasedModel` and follow its interface (see below). `ABM` is an alias to `AgentBasedModel`.

## Available concrete implementations

  * [`StandardABM`](@ref)
  * [`EventQueueABM`](@ref)

It is also straightforward to create your own versions of `AgentBasedModel`, see [the corresponding entry in the developer documentation](@ref make_new_model).

## Interface of `AgentBasedModel`

  * `step!(model, args...)` progress the model forwards in time.
  * `model[id]` returns the agent with given `id`.
  * `abmproperties(model)` returns the `properties` container storing model-level properties.
  * `model.property`:  If the model `properties` is a dictionary with key type `Symbol`, or if it is a composite type (`struct`), then the syntax `model.property` will return the model property with key `:property`.
  * `abmtime(model)` will return the current time of the model. All models start from time 0 and time is incremented as the model is [`step!`](@ref)-ped.
  * `abmrng(model)` will return the random number generator of the model. It is strongly recommended to give `abmrng(model)` to all calls to `rand` and similar functions, so that reproducibility can be established in your modelling workflow.
  * `allids(model)/allagents(model)` returns an iterator over all IDs/agents in the model.
  * `hasid(model, id)` returns `true` if the model has an agent with given `id`.

`AgentBasedModel` defines an extendable interface composed of the above syntax as well as a few more additional functions described in the Developer's Docs. Following this interface you can implement new variants of an `AgentBasedModel`. The interface allows instances of `AgentBasedModel` to be used with any of the [API](@ref). For example, functions such as [`random_agent`](@ref), [`move_agent!`](@ref) or [`add_agent!`](@ref) do not need to be implemented manually but work out of the box provided the `AgentBasedModel` interface is followed.
