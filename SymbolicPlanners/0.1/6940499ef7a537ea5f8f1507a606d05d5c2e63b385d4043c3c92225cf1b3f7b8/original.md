```
(sim::Simulator)(sol::Solution, domain::Domain, state::State, [spec])
```

Simulates the execution of `sol` in a PDDL `domain` starting from an initial `state`. A goal specification `spec` may be provided to serve as a terminating condition for the simulation, or to specify cost or reward information. 
