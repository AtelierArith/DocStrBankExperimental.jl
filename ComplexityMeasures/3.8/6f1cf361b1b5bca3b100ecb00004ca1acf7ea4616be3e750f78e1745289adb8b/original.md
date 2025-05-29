```
Outcome <: Number
Outcome(num::Integer)
```

A convenience wrapper around around an `Integer` that represents an unspecified but enumerated outcome. It exists to distinguish the case of generic outcomes (which  are allocated when using `counts`) vs actual integer outcomes (which may be allocated when using `counts_and_outcomes`). It is also used for pretty-printing `Counts` and  `Probabilities`.
