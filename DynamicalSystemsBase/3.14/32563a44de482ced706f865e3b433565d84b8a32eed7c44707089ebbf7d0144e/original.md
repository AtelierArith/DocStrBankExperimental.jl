```
poincaresos(ds::CoupledODEs, plane, T = 1000.0; kwargs...) → P::StateSpaceSet
```

Return the iterations of `ds` on the Poincaré surface of section with the `plane`, by evolving `ds` up to a total of `T`. Return a [`StateSpaceSet`](@ref) of the points that are on the surface of section.

This function initializes a [`PoincareMap`](@ref) and steps it until its [`current_crossing_time`](@ref) exceeds `T`. You can also use [`trajectory`](@ref) with [`PoincareMap`](@ref) to get a sequence of `N::Int` points instead.

The keywords `Ttr, save_idxs` act as in [`trajectory`](@ref). See [`PoincareMap`](@ref) for `plane` and all other keywords.
