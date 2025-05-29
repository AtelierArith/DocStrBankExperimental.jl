```julia
struct TalwarRho{δ} <: MLJLinearModels.RobustRho1P{δ}
```

Talwar weighing of the residuals corresponding to

$ρ(z) = z²/2$ if `|z|≤δ` and `ρ(z)=ρ(δ)` otherwise.

Note: symmetric weighing.
