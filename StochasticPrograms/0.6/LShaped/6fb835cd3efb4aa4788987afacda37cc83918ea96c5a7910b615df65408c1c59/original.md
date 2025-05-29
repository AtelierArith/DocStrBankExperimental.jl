```
Consolidation
```

Functor object for using consolidation in an L-shaped algorithm. Create by supplying a [`Consolidate`](@ref) object through `consolidate` in `LShaped.Optimizer` or by setting the [`Consolidator`](@ref) attribute.

...

# Algorithm parameters

  * `tresh::T` = 0.95: Relative amount of redundant cuts in a former iteration required to consider the iteration redundant
  * `at::Int = 5.0`: Number of times an iteration can be redundant before consolidation is triggered
  * `rebuild::Function = at_tolerance()`: Function deciding when the master model should be rebuilt according to performed consolidations

...
