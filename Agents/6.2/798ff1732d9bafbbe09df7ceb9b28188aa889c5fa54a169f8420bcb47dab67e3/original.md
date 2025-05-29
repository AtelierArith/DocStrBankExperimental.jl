```
EventQueueABM <: AgentBasedModel
```

A concrete implementation of an [`AgentBasedModel`](@ref) which operates in continuous time, in contrast with the discrete time nature of [`StandardABM`](@ref).

Here is a summary of how the time evolution of this model works:

A list of possible events that can be created is provided to the model. The events have four pieces of information:

1. The action that they perform once triggered. The action is a generic Julia function `action!(agent, model)` that will act on the agent corresponding to the event. Similarly with `agent_step!` for [`StandardABM`](@ref), this function may do anything and utilize any function from the Agents.jl [API](@ref) or the entire Julia ecosystem. The `action!` function may spawn new events by using [`add_event!`](@ref) function,  however the default behavior is to generate new events automatically, see below.
2. The propensity of the event. A propensity is a concept similar to a probability mass. When automatically generating a new event for an agent, first all applicable events for that agent are collected. Then, their propensities are calculated. The event generated then is selected randomly by weighting each possible event by its propensity.
3. The agent type(s) the event applies to. By default it applies to all types.
4. The timing of the event, i.e., when should it be triggered once it is generated. By default this is an exponentially distributed random variable divided by the propensity of the event. I.e., it follows a Poisson process with the propensity as the "rate". The timings of the events therefore establish the natural timescales of the ABM.

Events are scheduled in a temporally ordered queue, and once the model evolution time reaches the event time, the event is "triggered". This means that first the event action is performed on its corresponding agent. By default, once an event has finished its action, a new event is generated for the same agent (if the agent still exists), chosen randomly based on the propensities as discussed above. Then a time for the new event is generated and the new event is added back to the queue. In this way, an event always generates a new event after it has finished its action (by default; this can be overwritten). Keep in mind that the scheduling and triggering of events is agnostic to what the events actually do; even if an event does nothing, it would  still "use up" the agent's time if scheduled. You can avoid this by assigning propensity 0 to such events in the propensity function, according to the agent and model state.

`EventQueueABM` is a generalization of "Gillespie"-like simulations, offering more power and flexibility than a standard Gillespie simulation, while also allowing "Gillespie"-like configuration with the default settings.

Here is how to construct an `EventQueueABM`:

```
EventQueueABM(AgentType, events [, space]; kwargs...)
```

Create an instance of an [`EventQueueABM`](@ref).

The model expects agents of type `AgentType(s)` living in the given `space`. `AgentType(s)` is the result of [`@agent`](@ref) or `@multiagent` or a `Union` of agent types.

`space` is a subtype of `AbstractSpace`, see [Space](@ref available_spaces) for all available spaces.

`events` is a container of instances of [`AgentEvent`](@ref), which are the events that are scheduled and then affect agents. A `Tuple` or `NamedTuple` for `events` leads to optimal performance. The key type of `events` is also what is given as index to [`add_event!`](@ref).

By default, each time a new agent is added to the model via [`add_agent!`](@ref), a new event is generated based on the pool of possible events that can affect the agent. In this way the simulation can immediatelly start once agents have been added to the model. You can disable this behavior with a keyword. In this case, you need to manually use the function [`add_event!`](@ref) to add events to the queue so that the model can be evolved in time. (you can always use this function regardless of the default event scheduling behavior)

## Keyword arguments

  * `container, properties, rng, warn`: same as in [`StandardABM`](@ref).
  * `autogenerate_on_add::Bool = true`: whether to automatically generate a new event for an agent when the agent is added to the model.
  * `autogenerate_after_action::Bool = true`: whether to automatically generate a new event for an agent after an event affected said agent has been triggered.

!!! warn "No IO yet"
    This model does not yet support IO operations such as [`save_checkpoint`](@ref AgentsIO.save_checkpoint). Pull Requests that implement this are welcomed!

