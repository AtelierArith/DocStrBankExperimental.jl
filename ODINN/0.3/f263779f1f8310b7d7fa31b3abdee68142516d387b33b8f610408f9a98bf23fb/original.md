```
UDEparameters(; sensealg, optim_autoAD, grad, optimization_method, loss_type, empirical_loss_function, scale_loss, target) where {ADJ <: AbstractAdjointMethod}
```

Create a `UDEparameters` object for configuring the sensitivity analysis and optimization of a Universal Differential Equation (UDE).

# Keyword Arguments

  * `sensealg::SciMLBase.AbstractAdjointSensitivityAlgorithm`: The sensitivity algorithm to use for adjoint calculations. Defaults to `GaussAdjoint(autojacvec=SciMLSensitivity.EnzymeVJP())`.
  * `optim_autoAD::AbstractADType`: The automatic differentiation type for optimization. Defaults to `Optimization.AutoEnzyme()`.
  * `grad::ADJ`: The adjoint gradient computation method. Defaults to `SciMLSensitivityAdjoint()`.
  * `optimization_method::String`: The optimization method to use. Must be either `"AD+AD"` or `"AD+Diff"`. Defaults to `"AD+AD"`.
  * `loss_type::String`: The type of loss function to use. Must be either `"V"` (velocity) or `"H"` (thickness). Defaults to `"V"`.
  * `empirical_loss_function::AbstractLoss`: The loss function to use for optimization. Defaults to `L2Sum()`.
  * `scale_loss::Bool`: Whether to scale the loss function. Defaults to `true`.
  * `target::Union{Symbol, Nothing}`: The target variable for optimization. Defaults to `:A`.

# Returns

  * A `UDEparameters` object configured with the specified sensitivity, optimization, and loss settings.

# Description

This function creates a `UDEparameters` object that encapsulates the configuration for sensitivity analysis, optimization, and loss computation in a Universal Differential Equation (UDE) framework. It verifies that the provided `optimization_method` and `loss_type` are valid and constructs the solver parameters accordingly.

# Notes

  * The `optimization_method` must be either `"AD+AD"` (automatic differentiation for both forward and backward passes) or `"AD+Diff"` (automatic differentiation combined with finite differences).
  * The `loss_type` must be either `"V"` (velocity-based loss) or `"H"` (thickness-based loss).
  * The `empirical_loss_function` determines how the loss is computed during optimization.
