```
(sim::Simulator)(domain::Domain, state::State, actions, spec)
```

Simulates the execution of `actions` in a PDDL `domain` starting from an initial `state`. The goal specification `spec` serves as a terminating condition for the simulation, and may also specify cost or reward information.
