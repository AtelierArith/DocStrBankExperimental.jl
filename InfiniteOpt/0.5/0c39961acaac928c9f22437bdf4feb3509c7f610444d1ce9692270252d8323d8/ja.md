```
build_measure(expr::JuMP.AbstractJuMPScalar,
              data::AbstractMeasureData)::Measure
```

与えられた測定対象の式 `expr` を使用して、測定データ `data` に基づいて [`Measure`](@ref) を構築して返します。これは主に測定定義の内部メソッドとして機能します。`data` に関連付けられたサポートが、測定に含まれる有限変数の有限変数パラメータの境界に違反する場合はエラーが発生します。
