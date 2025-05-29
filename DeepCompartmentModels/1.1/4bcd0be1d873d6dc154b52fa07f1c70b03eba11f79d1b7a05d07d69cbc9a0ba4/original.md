```
DeepCompartmentModel{T,D,M,S}
```

Model architecture originally described in [janssen2022]. Originally uses a  neural network to learn the relationship between the covariates and the  parameters of a system of differential equations, which for example represents  a compartment model.

# Arguments

  * `problem::AbstractDEProblem`: DE problem describing the dynamical system.
  * `model`: Model to use for the prediction of DE parameters. The package focusses on the use of neural networks based on Lux.jl.
  * `T::Type`: DataType of parameters and predictions.
  * `dv_compartment::Int`: The index of the compartment for the prediction of the dependent variable. Default = 1.
  * `sensealg`: Sensitivity algorithm to use for the calculation of gradients of the parameters with respect to the DESolution.


[janssen2022] Janssen, Alexander, et al. "Deep compartment models: a deep learning approach for the reliable prediction of time‐series data in pharmacokinetic modeling." CPT: Pharmacometrics & Systems Pharmacology 11.7 (2022): 934-945.
