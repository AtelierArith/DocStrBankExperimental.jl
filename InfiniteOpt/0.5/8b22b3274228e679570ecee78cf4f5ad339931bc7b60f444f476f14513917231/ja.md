```
JuMP.delete(model::InfiniteModel,
            prefs::AbstractArray{<:DependentParameterRef})::Nothing
```

`JuMP.delete`を拡張して、依存する無限パラメータとその依存関係を削除します。`prefs`に依存するすべての変数、制約、および測定関数は、それらを除外するように更新されます。パラメータが測定に使用される`AbstractMeasureData`データ型に含まれている場合、測定が無効になるためエラーが発生します。したがって、この依存関係を含む測定は最初に削除する必要があります。カスタム`AbstractMeasureData`データ型が使用される場合にパラメータの削除を許可するために、[`parameter_refs`](@ref parameter_refs(::AbstractMeasureData))を拡張する必要があります。依存する無限変数は、[`reset_start_value_function`](@ref)を介して開始値がデフォルトにリセットされることに注意してください。

**例**

```julia-repl
julia> print(model)
Min measure(g(t, x)*t + x) + z
Subject to
 z ≥ 0.0
 g(t, x) + z ≥ 42.0, ∀ t ∈ [0, 6], x[1] ∈ [-1, 1], x[2] ∈ [-1, 1]
 g(0.5, x) = 0, x[1] ∈ [-1, 1], x[2] ∈ [-1, 1]

julia> delete(model, x)

julia> print(model)
Min measure(g(t)*t) + z
Subject to
 g(t) + z ≥ 42.0, ∀ t ∈ [0, 6]
 g(0.5) = 0
```
