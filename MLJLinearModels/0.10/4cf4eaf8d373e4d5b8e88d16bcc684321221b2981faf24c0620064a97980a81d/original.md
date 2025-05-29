```julia
struct AndrewsRho{δ} <: MLJLinearModels.RobustRho1P{δ}
```

Andrews weighing of the residuals corresponding to

$ρ(z) = -cos(πz/δ)/(π/δ)²$ if `|z|≤δ` and `ρ(δ)` otherwise.

Note: symmetric weighing.
