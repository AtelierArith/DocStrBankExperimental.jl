```
DeepCompartmentModel(ode_fn, model, error, T=Float32; kwargs...)
```

Convenience constructor that internally creates an ODEProblem based on the  passed ode*fn. Attempts to estimate the number of partial differential equations present in the ode*fn.

# Arguments

  * `ode_fn::Function`: Function that describes the dynamical system.
  * `model`: Model to use for the prediction of DE parameters. The package focusses on the use of neural networks based on Lux.jl.
  * `error::AbstractErrorModel`: Error model to use. Should be one of [ImplicitError, AdditiveError, ProportionalError, CombinedError, CustomError].
  * `T::Type`: DataType of parameters and predictions.

# Keyword arguments

  * `dv_compartment::Int`: The index of the compartment for the prediction of the dependent variable. Default = 1.
  * `sensealg`: Sensitivity algorithm to use for the calculation of gradients of the parameters with respect to the DESolution.
