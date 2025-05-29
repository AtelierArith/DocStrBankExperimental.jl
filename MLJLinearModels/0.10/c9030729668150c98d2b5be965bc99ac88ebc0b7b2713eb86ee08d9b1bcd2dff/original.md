```julia
struct HuberRho{δ} <: MLJLinearModels.RobustRho1P{δ}
```

Huber weighing of the residuals corresponding to

$ρ(z) = z²/2$  if `|z|≤δ` and `ρ(z)=δ(|z|-δ/2)` otherwise.

Note: symmetric weighing.
