```
direct_model(factory::MOI.OptimizerWithAttributes)
```

`factory`を使用して[`direct_model`](@ref)を作成します。これは[`optimizer_with_attributes`](@ref)によって作成された`MOI.OptimizerWithAttributes`オブジェクトです。

## 例

```julia
model = direct_model(
    optimizer_with_attributes(
        Gurobi.Optimizer,
        "Presolve" => 0,
        "OutputFlag" => 1,
    )
)
```

は次のように等価です:

```julia
model = direct_model(Gurobi.Optimizer())
set_optimizer_attribute(model, "Presolve", 0)
set_optimizer_attribute(model, "OutputFlag", 1)
```
