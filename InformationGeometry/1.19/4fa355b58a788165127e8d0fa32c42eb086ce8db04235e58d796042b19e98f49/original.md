```
RicciScalar(DM::DataModel, θ::AbstractVector; BigCalc::Bool=false) -> Real
RicciScalar(Metric::Function, θ::AbstractVector; BigCalc::Bool=false) -> Real
```

Calculates the Ricci scalar by finite differencing of the `Metric`. `BigCalc=true` increases accuracy through `BigFloat` calculation.
