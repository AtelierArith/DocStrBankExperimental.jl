```
difference_of_convex_algorithm!(M, f, g, ∂h, p; kwargs...)
difference_of_convex_algorithm!(M, mdco, p; kwargs...)
```

Run the difference of convex algorithm and perform the steps in place of `p`. See [`difference_of_convex_algorithm`](@ref) for more details.

if you specify the [`ManifoldDifferenceOfConvexObjective`](@ref) `mdco`, the `g` is a keyword argument.
