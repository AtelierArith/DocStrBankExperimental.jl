An abstract type for state space models.

Any concrete subtype of `AbstractStateSpaceModel` should implement a method for `AbstractMCMC.sample` which performs forward simulation. For an example implementation, see [AbstractMCMC.sample(::StateSpaceModel)](@ref).

For most regular use-cases, the predefined `StateSpaceModel` type, documented below, should be sufficient.
