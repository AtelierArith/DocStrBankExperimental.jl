```
analytic_expansion(expr, data::AbstractMeasureData,
                   write_model::JuMP.AbstractModel)::JuMP.AbstractJuMPScalar
```

解析的に、測定を評価します。これは、測定式 `expr` が `data` に依存せず、したがって `expr` が `data` の解析結果と共に定数として扱える単純なケースです。これは、[`expand`](@ref) および [`expand_measures`](@ref) によって使用される内部メソッドとして意図されています。認識されていない `data` タイプの場合は、代わりに `expand_measure` が呼び出されます。ユーザー定義の測定データ型は、必要に応じてこのメソッドを拡張することを選択できます。これは `is_analytic(mref) = true` のときにトリガーされます。
