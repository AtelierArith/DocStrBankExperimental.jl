```
poincaresos(A::AbstractStateSpaceSet, plane; kwargs...) → P::StateSpaceSet
```

Calculate the Poincaré surface of section of the given dataset with the given `plane` by performing linear interpolation betweeen points that sandwich the hyperplane.

Argument `plane` and keywords `direction, warning, save_idxs` are the same as in [`PoincareMap`](@ref).
