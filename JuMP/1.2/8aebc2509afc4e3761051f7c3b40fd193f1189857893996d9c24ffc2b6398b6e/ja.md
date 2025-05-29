```
set_objective_function(
    model::Model,
    func::Union{AbstractJuMPScalar, MathOptInterface.AbstractScalarFunction})
```

モデルの目的関数を指定された関数に設定します。目的の感覚を設定するには、[`set_objective_sense`](@ref)を参照してください。これらは低レベルの関数です。目的を設定する推奨方法は、[`@objective`](@ref)マクロを使用することです。
