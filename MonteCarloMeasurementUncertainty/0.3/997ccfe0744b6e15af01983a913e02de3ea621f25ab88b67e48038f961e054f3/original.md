```
MonteCarloMeasurement
```

Abstract type that provides an interface for all `MonteCarloMeasurement`s.

!!! warning
    ### Required Interface Functions

    The following *functions* **must** have `methods` defined for each new `MonteCarloMeasurement`.

      * [`push!`](@ref): Move a new measurement into the `MonteCarloMeasurement` instance.


!!! note
    ### Default Interface Functions

    The following *functions* have a default `method` for any given `MonteCarloMeasurement`.

      * [`name`](@ref): Define a `name` for a given `MonteCarloMeasurement` instance.
      * [`measurement`](@ref): Construct a measurement from [`Measurements.jl`](https://github.com/JuliaPhysics/Measurements.jl).

