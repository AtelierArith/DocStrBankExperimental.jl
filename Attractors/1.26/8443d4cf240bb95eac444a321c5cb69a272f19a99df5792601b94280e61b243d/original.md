```
MatchByBasinEnclosure(; kw...) <: IDMatcher
```

A matcher that matches attractors by whether they are enclosed in the basin of a new attractor or not.

## Keyword arguments

  * `ε = nothing`: distance threshold given to [`AttractorsViaProximity`](@ref). If `nothing`, it is estimated as a quarter of the minimum distance of centroids (in contrast to the default more accurate estimation in [`AttractorsViaProximity`](@ref)).
  * `Δt = 1, consecutive_lost_steps = 1000`: also given to [`AttractorsViaProximity`](@ref). We have not yet decided what should happen to attractors that did not converge to one of the current attractors within this number of steps. At the moment they get assigned the next available free ID but this may change in future releases.
  * `distance = Centroid()`: metric to estimate distances between state space sets in case there are co-flowing attractors, see below.
  * `seeding = A -> A[end]`: how to select a point from the attractor to see if it is enclosed in the basin of a new attractor.

## Description

An attractor `A₋` is a set in a state space that occupies a particular region (or, a single point, if it is a fixed point). This region is always within the basin of attraction of said attractor. When the parameter of the dynamical system is incremented, the attractors `A₊` in the new parameter have basins that may have changed in shape and size.

The new attractor `A₊` is "matched" (i.e., has its ID changed) to the old attractor `A₋` attractor if `A₋` is located inside the basin of attraction of `A₊`. To see if `A₋` is in the basin of `A₊`, we first pick a point from `A₋` using the `seeding` keyword argument. By default this is the last point on the attractor, but it could be anything else, including the centroid of the attractor (`mean(A)`). This point is given as an initial condition to an [`AttractorsViaProximity`](@ref) mapper that maps initial conditions to the `₊` attractors when the trajectories from the initial conditions are `ε`-close to the `₊` attractors.

There can be the situation where multiple `₋` attractors converge to the same `₊` attractor, which we call "coflowing attractors". In this scenario matching is prioritized for the `₋` attractor that is closest to the `₊` in terms of state space set distance, which is estimated with the `distance` keyword, which can be anything [`MatchBySSSetDistance`](@ref) accepts. The closest `₊` attractor gets the ID of the `₋` closest attractor that converge to it.

Basin enclosure is a concept similar to "basin (in)stability" in [Ritchie2023](@cite): attractors that quantify as "basin stable" are matched.
