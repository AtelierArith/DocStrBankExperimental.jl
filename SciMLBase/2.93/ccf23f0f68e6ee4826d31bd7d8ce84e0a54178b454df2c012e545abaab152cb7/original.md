```julia
struct CallbackSet{T1<:Tuple, T2<:Tuple} <: SciMLBase.DECallback
```

Multiple callbacks can be chained together to form a `CallbackSet`. A `CallbackSet` is constructed by passing the constructor `ContinuousCallback`, `DiscreteCallback`, `VectorContinuousCallback` or other `CallbackSet` instances:

```
CallbackSet(cb1,cb2,cb3)
```

You can pass as many callbacks as you like. When the solvers encounter multiple callbacks, the following rules apply:

  * `ContinuousCallback`s and `VectorContinuousCallback`s are applied before `DiscreteCallback`s. (This is because they often implement event-finding that will backtrack the timestep to smaller than `dt`).
  * For `ContinuousCallback`s and `VectorContinuousCallback`s, the event times are found by rootfinding and only the first `ContinuousCallback` or `VectorContinuousCallback` affect is applied.
  * The `DiscreteCallback`s are then applied in order. Note that the ordering only matters for the conditions: if a previous callback modifies `u` in such a way that the next callback no longer evaluates condition to `true`, its `affect` will not be applied.
