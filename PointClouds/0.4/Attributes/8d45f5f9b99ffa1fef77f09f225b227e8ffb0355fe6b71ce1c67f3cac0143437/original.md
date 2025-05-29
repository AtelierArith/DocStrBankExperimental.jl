```
apply(f::Function, [T], p::PointCloud, attrs...; kws...)
```

Apply a function `f` to the attributes `attrs` of each point in `p`. The attribute names are passed as `Symbol`s and the function should take one argument for each attribute name.

The element type of the output is determined automatically from the function and the argument types. It can also be set with the `T` argument in case the automatically determined type is too narrow or too wide.

# Keywords

  * `neighbors`: Apply function to the attribute of a point’s neighbors rather than its own, if set to `true` or to an integer `k`. The function `f` receives `AbstractVector`s with the attribute values of the neighbors in that case. The indices of the `k` nearest neighbors are read from `p.neighbors` if available (see [`neighbors`](@ref)/[`neighbors!`](@ref)). If `p.neighbors` is unavailable or contains fewer than `k` indices, the neighbor search is (re)run (without updating `p.neighbors`). Default: `false`
