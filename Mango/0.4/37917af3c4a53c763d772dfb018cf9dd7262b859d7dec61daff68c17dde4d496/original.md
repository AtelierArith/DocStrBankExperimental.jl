```
on_step(agent::Agent, world::World, clock::Clock, step_size_s::Real)
```

Hook-in, called on every step of the simulation container for every `agent`.

Further, the `world` is passed, which represents a common view on the environment in which agents can interact with eachother. Besides, the `clock` and the `step_size_s` can be used to read the current simulation time and the time which passes in the current step.
