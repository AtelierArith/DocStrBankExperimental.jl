```
minimal_critical_shock(mapper::AttractorMapper, u0, search_area, algorithm; kw...)
```

Return the *minimal critical shock* for the initial point `u0` according to the specified `algorithm` given a `mapper` that satisfies the `id = mapper(u0)` interface (see [`AttractorMapper`](@ref) if you are not sure which mappers do that). The output `mfs` is a vector like `u0`.

The `mapper` contains a reference to a [`DynamicalSystem`](@ref). The options for `algorithm` are: [`MCSBruteForce`](@ref) or [`MCSBlackBoxOptim`](@ref). For high dimensional systems [`MCSBlackBoxOptim`](@ref) is likely more accurate.

The `search_area` dictates the state space range for the search of the `mfs`. It can be a 2-tuple of (min, max) values, in which case the same values are used for each dimension of the system in `mapper`. Otherwise, it can be a vector of 2-tuples, each for each dimension of the system. The search area is defined w.r.t. to `u0` (i.e., it is the search area for perturbations of `u0`).

An alias to `minimal_critical_shock` is `excitability_threshold`. Other names for the concept are or *stability threshold* or *minimal fatal shock*.

## Keyword arguments

  * `metric = LinearAlgebra.norm`: a metric function that gives the norm of a perturbation vector. This keyword is ignored for the [`MCSBruteForce`](@ref) algorithm.
  * `target_id = nothing`: when not `nothing`, it should be an integer or a vector of integers corresponding to target attractor label(s). Then, the MFS is estimated based only on perturbations that lead to the target attractor(s).

## Description

The minimal critical shock is defined as the smallest-norm perturbation of the initial point `u0` that will lead it a different basin of attraction than the one it was originally in. This alternative basin is not returned, do `mapper(u0 .+ mfs)` if you need the ID.

The minimal critical shock has many names. Many papers computed this quantity without explicitly naming it, or naming it something simple like "distance to the threshold". The first work that proposed the concept as a nonlocal stability quantifier was by [Klinshov2015](@cite) with the name "stability threshold". Here we use the name of [Halekotte2020](@cite).

Our implementation is generic and works for *any* dynamical system, using either black box optimization or brute force searching approaches and the unique interface of Attractors.jl for mapping initial conditions to attractors. In contrast to [Klinshov2015](@cite) or [Halekotte2020](@cite), our implementation does not place any assumptions on the nature of the dynamical system, or whether the basin boundaries are smooth.

The *excitability threshold* is a concept nearly identical, however, instead of looking for a perturbation that simply brings us out of the basin, we look for the smallest perturbation that brings us into specified basin(s). This is enabled via the keyword `target_id`.
