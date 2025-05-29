make_jacobian(model::AbstractModel)

Creates and returns a function which updates the auxiliary variables `p` in place and then updates the entries of the Jacobian matrix `W` for the `model` in place.

The default is that no updates are required, no implicit tendency is present, and hence the timestepping is entirely explicit.

Note that the returned function `jacobian!` should be used as `Wfact!` in `ClimaTimeSteppers.jl` and `SciMLBase.jl`.
