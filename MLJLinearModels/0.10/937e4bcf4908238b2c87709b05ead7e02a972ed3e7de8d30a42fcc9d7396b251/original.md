```julia
struct BisquareRho{δ} <: MLJLinearModels.RobustRho1P{δ}
```

Bisquare weighing of the residuals corresponding to

$ρ(z) = δ²/6 (1-(1-(z/δ)²)³)$ if `|z|≤δ` and `δ²/6` otherwise.

Note: symmetric weighing.
