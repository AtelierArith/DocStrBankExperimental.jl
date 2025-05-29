```julia
struct FairRho{δ} <: MLJLinearModels.RobustRho1P{δ}
```

Fair weighing of the residuals corresponding to

$ρ(z) = δ² (|z|/δ - log(1+|z|/δ))$

Note: symmetric weighing.
