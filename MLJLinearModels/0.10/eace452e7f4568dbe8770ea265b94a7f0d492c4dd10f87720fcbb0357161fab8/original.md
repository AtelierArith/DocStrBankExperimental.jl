```julia
struct QuantileRho{δ} <: MLJLinearModels.RobustRho1P{δ}
```

Quantile regression weighing of the residuals corresponding to

$ρ(z) = -z(δ - 1(z>=0))$

Note: asymetric weighing, the "-" sign is because similar libraries like quantreg for instance define the residual as `y-Xθ` while we do the opposite (out of convenience for gradients etc).
