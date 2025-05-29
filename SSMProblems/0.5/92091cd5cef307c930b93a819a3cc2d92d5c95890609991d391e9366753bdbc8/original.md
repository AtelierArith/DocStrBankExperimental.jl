Latent dynamics of a state space model.

Any concrete subtype of `LatentDynamics` should implement the functions `logdensity` and `simulate`, by defining two methods as documented below, one for initialisation and one for transitioning. Whether each of these functions need to be implemented depends on the exact inference algorithm that is intended to be used.

Alternatively, you may specify methods for the function `distribution` which will be used to define the above methods.

All of these methods should accept keyword arguments through `kwargs...` to facilitate inference-time dependencies of the dynamics as explained in [Control Variables and Keyword Arguments](@ref).

The latent states should be of type `ET` which should be a composed from `T`, the arithmetic type used for the dynamics (e.g. Float32, ForwardDiff.Dual).

# Parameters

  * `T`: The arithmetic type of the latent dynamics.
  * `ET`: The element type of the latent dynamics.
