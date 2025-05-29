```
Ricci(DM::DataModel, θ::AbstractVector; BigCalc::Bool=false)
Ricci(Metric::Function, θ::AbstractVector; BigCalc::Bool=false)
```

Calculates the components of the $(0,2)$ Ricci tensor by finite differencing of the `Metric`. `BigCalc=true` increases accuracy through `BigFloat` calculation.
