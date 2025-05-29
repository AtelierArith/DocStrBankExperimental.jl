```julia
struct LogisticRho{δ} <: MLJLinearModels.RobustRho1P{δ}
```

Logistic weighing of the residuals corresponding to

$ρ(z) = δ² log(cosh(z/δ))$

Note: symmetric weighing.
