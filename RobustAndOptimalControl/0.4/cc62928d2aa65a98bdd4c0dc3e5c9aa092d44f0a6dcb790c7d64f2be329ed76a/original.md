```
nu_reduction_recursive(G, g = 0.1; gap = nugap(G), keepinds = Set{Int}(1), verbose = false)
```

Find a νgap cover of balls of radius `g` (in the νgap metric) that contain all realizations in `G`. 

If the `gap = nugap(G)` has already been precomputed, it can be supplied as an argument to avoid potentially costly recomputaiton. If a manually computed `gap` is supplied, you must also supply `keepinds=Set{Int}(index)` where `index` is the index of the nominal system in `G` used to compute `gap`.

The returned cover `Gr` is of the same type as `G`, but with a smaller number of particles. A controller designed for `Gr` that achieves a [`ncfmargin`](@ref) of at least `g` for all realizations in `Gr` will stabilize all realizations in the original `G`. The extreme case cover where `Gr = Gnominal` is a single realization only can be computed by calling `g = nugap(G, i)` where `i` is the index of the nominal system in `G`.

# Arguments:

  * `G`: An uncertain model in the form of a `StateSpace{TE, Particles}` (a multi-model).
  * `g`: The radius of the balls in the νgap cover.
  * `gap`: An optional precomputed gap
  * `verbose`: Print progress
