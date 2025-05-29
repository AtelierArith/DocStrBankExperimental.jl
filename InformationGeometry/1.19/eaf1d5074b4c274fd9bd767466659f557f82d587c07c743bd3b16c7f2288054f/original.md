```
Riemann(DM::DataModel, θ::AbstractVector; BigCalc::Bool=false)
Riemann(Metric::Function, θ::AbstractVector; BigCalc::Bool=false)
```

Calculates the components of the $(1,3)$ Riemann tensor by finite differencing of the `Metric`. `BigCalc=true` increases accuracy through BigFloat calculation.
