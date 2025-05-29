```
fixedpoints(ds::CoreDynamicalSystem, box, J = nothing; kwargs...) → fp, eigs, stable
```

Return all fixed points `fp` of the given out-of-place `ds` (either `DeterministicIteratedMap` or `CoupledODEs`) that exist within the state space subset `box` for parameter configuration `p`. Fixed points are returned as a [`StateSpaceSet`](@ref). For convenience, a vector of the Jacobian eigenvalues of each fixed point, and whether the fixed points are stable or not, are also returned.

`box` is an appropriate interval box from IntervalRootFinding.jl (a vector of intervals). E.g. for a 3D system it would be something like

```julia
v, z = interval(-5, 5), interval(-2, 2)  # 1D intervals
box = [v, v, z]
```

`J` is the Jacobian of the dynamic rule of `ds`. It is like in [`TangentDynamicalSystem`](@ref), however in this case automatic Jacobian estimation does not work, hence a hand-coded version must be given.

Internally IntervalRootFinding.jl is used and as a result we are guaranteed to find all fixed points that exist in `box`, regardless of stability. Since IntervalRootFinding.jl returns an interval containing a unique fixed point, we return the midpoint of the interval as the actual fixed point. Naturally, limitations inherent to IntervalRootFinding.jl apply here.

The output of `fixedpoints` can be used in the [BifurcationKit.jl](https://github.com/rveltz/BifurcationKit.jl) as a start of a continuation process. See also [`periodicorbits`](@ref).

## Keyword arguments

  * `method = IntervalRootFinding.Krawczyk` configures the root finding method, see the docs of IntervalRootFinding.jl for all possibilities.
  * `tol = 1e-15` is the root-finding tolerance.
  * `warn = true` throw a warning if no fixed points are found.
  * `order = nothing` search for fixed points of the n-th iterate of [`DeterministicIteratedMap`](@ref). Must be a positive integer or `nothing`. Select `nothing` or 1 to search for the fixed points of the original map.

## Performance notes

Setting `order` to a value greater than 5 can be very slow. Consider using more suitable algorithms for periodic orbit detection, such as [`periodicorbits`](@ref).
