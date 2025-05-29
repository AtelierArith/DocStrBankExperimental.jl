```
Chain(rules...)
Chain(rules::Tuple)
```

`Chain`s allow chaining rules together to be completed in a single processing step, without intermediate reads or writes from grids.

They are potentially compiled together into a single function call, especially if you use `@inline` on all `applyrule` methods. `Chain` can hold either all [`CellRule`](@ref) or [`NeighborhoodRule`](@ref) followed by [`CellRule`](@ref).

[`SetRule`](@ref) can't be used in `Chain`, as it doesn't have a return value.

![Chain rule diagram](https://raw.githubusercontent.com/cesaraustralia/DynamicGrids.jl/media/Chain.png)
