```
JuMP.delete(model::InfiniteModel, pref::ScalarParameterRef)::Nothing
```

`JuMP.delete`を拡張してスカラー パラメータとその依存関係を削除します。`pref`に依存するすべての変数、制約、および測定関数は、それを除外するように更新されます。パラメータが無限変数によって使用されている場合や、測定に使用される`AbstractMeasureData`データ型に含まれている場合はエラーが発生します。そうでないと、測定が無効になるためです。この依存関係を含む測定は、最初に削除する必要があります。カスタム`AbstractMeasureData`データ型が使用されている場合にパラメータの削除を許可するために、[`parameter_refs`](@ref parameter_refs(::AbstractMeasureData))を拡張する必要があることに注意してください。

**例**

```julia-repl
julia> delete(model, x)
```
