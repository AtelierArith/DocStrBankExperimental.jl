```
BigM{T} <: AbstractReformulationMethod
```

A type for using the big-M reformulation approach for disjunctive constraints.

**Fields**

  * `value::T`: Big-M value (default = `1e9`).
  * `tight::Bool`: Attempt to tighten the Big-M value (default = `true`)?
