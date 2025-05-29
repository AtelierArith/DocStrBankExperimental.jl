```
struct GridSearch{F,G}
```

Struct for a `GridSearch`.

# Fields

  * `f::F`: The function to optimise, of the form `f(x, p)`.
  * `p::P`: The arguments `p` in the function `f`.
  * `grid::G`: The grid, where `G<:AbstractGrid`. See also [`grid_search`](@ref).
