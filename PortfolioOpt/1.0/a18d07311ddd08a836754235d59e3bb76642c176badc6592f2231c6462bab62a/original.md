```
market_model(market::VolumeMarket{T,N}, optimizer_factory::Function) -> JuMP.Model, Vector{VariableRef}
```

Creates a JuMP model with appropriate PO variable and constraints:     - Investment vector of variables `w` (portfolio weights if `budget = 1`).     - Invested monney should be lower budget.

Returns the model and the reference to the vector of decision variables (length N).

Aditional arguments:

  * `optimizer_factory`: callable with zero arguments and return an empty `MathOptInterface.AbstractOptimizer``.
