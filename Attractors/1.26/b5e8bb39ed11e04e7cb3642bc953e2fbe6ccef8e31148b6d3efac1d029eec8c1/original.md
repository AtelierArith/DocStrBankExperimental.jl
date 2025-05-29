```
AttractorsViaFeaturizing(
    ds::DynamicalSystem, featurizer::Function,
    grouping_config = GroupViaClustering(); kwargs...
)
```

Initialize a `mapper` that maps initial conditions to attractors using a featurizing and grouping approach. This is a supercase of the featurizing and clustering approach that is utilized by bSTAB [Stender2021](@cite) and MCBB [Gelbrecht2020](@cite). See [`AttractorMapper`](@ref) for how to use the `mapper`. This `mapper` also allows the syntax `mapper(u0)` but only if the `grouping_config` is *not* `GroupViaClustering`.

`featurizer` is a function `f(A, t)` that takes as an input an integrated trajectory `A::StateSpaceSet` and the corresponding time vector `t` and returns a vector `v` of features describing the trajectory. For better performance, it is strongly recommended that `v isa SVector{<:Real}`.

`grouping_config` is an instance of any subtype of [`GroupingConfig`](@ref) and decides how features will be grouped into attractors, see below.

See also the intermediate functions [`extract_features`](@ref) and [`group_features`](@ref), which can be utilized when wanting to work directly with features.

## Keyword arguments

  * `T=100, Ttr=100, Δt=1`: Propagated to `DynamicalSystems.trajectory` for integrating an initial condition to yield `A, t`.
  * `threaded = true`: Whether to run the generation of features over threads by integrating trajectories in parallel.

## Description

The trajectory `X` of an initial condition is transformed into features. Each feature is a number useful in *characterizing the attractor* the initial condition ends up at, and **distinguishing it from other attractors**. Example features are the mean or standard deviation of some the dimensions of the trajectory, the entropy of some of the dimensions, the fractal dimension of `X`, or anything else you may fancy.

All feature vectors (each initial condition = 1 feature vector) are then grouped using one of the sevaral available grouping configurations. Each group is assumed to be a unique attractor, and hence each initial condition is labelled according to the group it is part of. The method thus relies on the user having at least some basic idea about what attractors to expect in order to pick the right features, and the right way to group them, in contrast to [`AttractorsViaRecurrences`](@ref).

Attractors are stored and can be accessed with [`extract_attractors`](@ref), however it should be clear that this mapper never actually finds attractors. They way we store attractors is by picking the first initial condition that belongs to the corresponding "attractor group", and then recording its trajectory with the same arguments `T, Ttr, Δt`. This is stored as the attractor, but of course there is no guarantee that this is actually an attractor.
