```
ChristoffelSymbol(DM::DataModel, θ::AbstractVector; BigCalc::Bool=false)
ChristoffelSymbol(Metric::Function, θ::AbstractVector; BigCalc::Bool=false)
```

Calculates the components of the $(1,2)$ Christoffel symbol $\Gamma$ at a point $\theta$ (i.e. the Christoffel symbol "of the second kind") through finite differencing of the `Metric`. Accurate to ≈ 3e-11. `BigCalc=true` increases accuracy through `BigFloat` calculation.
