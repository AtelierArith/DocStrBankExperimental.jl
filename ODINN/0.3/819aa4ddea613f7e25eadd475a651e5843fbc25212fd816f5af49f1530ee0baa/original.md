A mutable struct that holds parameters for a UDE (Universal Differential Equation).

```
UDEparameters{ADJ <: AbstractAdjointMethod} <: AbstractParameters
```

# Fields

  * `sensealg::SciMLBase.AbstractAdjointSensitivityAlgorithm`: The sensitivity algorithm used for adjoint sensitivity analysis.
  * `optimization_method::String`: The optimization method to be used.
  * `loss_type::String`: The type of loss function to be used.
  * `scale_loss::Bool`: A boolean indicating whether to scale the loss.
  * `target::Symbol`: The target variable for the optimization.
