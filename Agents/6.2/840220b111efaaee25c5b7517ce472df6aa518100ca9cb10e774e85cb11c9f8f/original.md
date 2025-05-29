```
AgentEvent(; action!, propensity, kinds, timing)
```

An event instance that can be given to [`EventQueueABM`](@ref).

  * `action! = dummystep`: is the function `action!(agent, model)` that will act on the agent the event corresponds to. This keyword is mandatory. The `action!` function may call [`add_event!`](@ref) to generate new events, regardless of the automatic generation of events by Agents.jl.
  * `propensity = 1.0`: it can be either a constant real number, or a function `propensity(agent, model)` that returns the propensity of the event. This function is called when a new event is generated for the given `agent`.
  * `types = AbstractAgent`: the types of agents the `action!` function can be applied to.
  * `timing = Agents.exp_propensity`: decides how long after its generation the event should trigger. By default the time is a randomly sampled time from an exponential distribution with parameter the total propensity of all applicable events to the agent. I.e., by default the "Gillespie" algorithm is used to time the events. Alternatively, it can be a custom function `timing(agent, model, propensity)` which will return the time.

Notice that when using the [`add_event!`](@ref) function, `propensity, timing` are ignored if `event_idx` and `t` are given.
