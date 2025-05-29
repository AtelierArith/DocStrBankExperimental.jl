Observation process of a state space model.

Any concrete subtype of `ObservationProcess` must implement the `logdensity` method, as defined below. Optionally, it may also implement `simulate` for use in forward simulation of the state space model.

Alternatively, you may specify a method for `distribution`, which will be used to define both of the above methods.

All of these methods should accept keyword arguments through `kwargs...` to facilitate inference-time dependencies of the observations as explained in [Control Variables and Keyword Arguments](@ref).

The observations should be of type `ET` which should be a composed from `T`, the arithmetic type used for the observations (e.g. Float32, ForwardDiff.Dual).

# Parameters

  * `T`: The arithmetic type of the observation process.
  * `ET`: The element type of the observation process.
