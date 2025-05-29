```
expand_measures(expr, write_model::JuMP.AbstractModel)::JuMP.AbstractJuMPScalar
```

`expr`内のすべての`MeasureRef`を[`expand_measure`](@ref)を介してインプレースで展開し、展開された式を返します。これは、[`expand_all_measures!`](@ref)および`TranscriptionOpt`によって使用される内部メソッドですが、`expand_measure`と組み合わせて[`add_point_variable`](@ref)/[`add_semi_infinite_variable`](@ref)を実装するユーザー定義の最適化モデル拡張にとって便利です。`write_model`は、[`expand_measure`](@ref)で説明されているように、測定変数が追加されるモデルです。
