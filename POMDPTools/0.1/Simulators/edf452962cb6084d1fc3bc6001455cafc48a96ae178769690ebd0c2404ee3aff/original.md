```
Sim(m::POMDP, p::Policy, metadata=(note="a note",))
Sim(m::POMDP, p::Policy[, updater[, initial_belief[, initialstate]]]; kwargs...)
```

Create a `Sim` object that represents a POMDP simulation.
