```
StandardABM <: AgentBasedModel
```

A concrete implementation of an [`AgentBasedModel`](@ref), which is also the most commonly used in agent based modelling studies. It operates in discrete time. As input, it requires at least one, or at most two functions: an agent stepping function and a model stepping function. At each discrete step of the simulation, the agent stepping function is applied once to all scheduled agents, and the model stepping function is applied once to the model.

See also [`EventQueueABM`](@ref) for a continuous time variant.

To construct a `StandardABM` use the syntax:

```
StandardABM(AgentType(s) [, space]; properties, agent_step!, model_step!, kwargs...)
```

The model expects agents of type `AgentType(s)` living in the given `space`. `AgentType(s)` is the result of [`@agent`](@ref) or `@multiagent` or a `Union` of agent types.

`space` is a subtype of `AbstractSpace`, see [Space](@ref available_spaces) for all available spaces. If it is omitted then all agents are virtually in one position and there is no spatial structure. Spaces are mutable objects and are not designed to be shared between models. Create a fresh instance of a space with the same properties if you need to do this.

The evolution rules are functions given to the keywords `agent_step!`, `model_step!`.

## Keywords

  * `agent_step!`: the optional agent stepping function that must be in the form `agent_step!(agent, model)` and is called for each scheduled `agent`.
  * `model_step!`: the optional model stepping function that must be in the form `model_step!(model)`. At least one of `agent_step!` or `model_step!` must be given. For complicated models, it could be more suitable to use only `model_step!` to evolve the model, see below the "advanced stepping" example.
  * `container = Dict`: the type of container the agents are stored at. Use `Vector` if no agents are removed during the simulation. This allows storing agents more efficiently, yielding faster retrieval and iteration over agents. Use `Dict` if agents are expected to be removed during the simulation.
  * `properties = nothing`: additional model-level properties that the user may include in the model. `properties` can be an arbitrary container of data, however it is most typically a `Dict` with `Symbol` keys, or a composite type (`struct`).
  * `scheduler = Schedulers.fastest`: is the scheduler that decides the (default) activation order of the agents. See the [scheduler API](@ref Schedulers) for more options. By default all agents are activated once per step in the fastest sequence possible. `scheduler` is completely ignored if no `agent_step!` function is given, as it is assumed that in this case the user takes control of scheduling, e.g., as in the "advanced stepping" example below.
  * `rng = Random.default_rng()`: the random number generator stored and used by the model in all calls to random functions. Accepts any subtype of `AbstractRNG`.
  * `agents_first::Bool = true`: whether to schedule and activate agents first and then call the `model_step!` function, or vice versa. Ignored if no `agent_step!` is given.
  * `warn=true`: some type tests for `AgentType(s)` are done, and by default warnings are thrown when appropriate.

## [Advanced stepping](@id advanced_stepping)

Some advanced models may require special handling for scheduling, or may need to schedule agents several times and act on different subsets of agents with different functions during a single simulation step. In such a scenario, it is more sensible to provide only a model stepping function, where all the dynamics is contained within.

Note that if you do not use the automated `agent_step!` option, you need to manually check for removed agents during evolution, using the [`hasid`](@ref) function.

Here is an example:

```julia
function complex_model_step!(model)
    # tip: these schedulers should be defined as properties of the model
    scheduler1 = Schedulers.Randomly()
    scheduler2 = user_defined_function_with_model_as_input
    for id in scheduler1(model)
        agent_step1!(model[id], model)
    end
    intermediate_model_action!(model)
    for id in scheduler2(model)
        # here `agent_step2!` may delete agents, so we check for it manually
        hasid(model, id) || continue
        agent_step2!(model[id], model)
    end
    if model.step_counter % 100 == 0
        model_action_every_100_steps!(model)
    end
    final_model_action!(model)
    return
end
```
