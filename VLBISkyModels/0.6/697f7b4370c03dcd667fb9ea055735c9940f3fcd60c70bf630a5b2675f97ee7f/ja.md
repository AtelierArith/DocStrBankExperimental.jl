```julia
struct PolarizedModel{TI, TQ, TU, TV} <: ComradeBase.AbstractPolarizedModel
```

偏光モデルのラップされたモデル。これは画像のストークス表現を使用します。

# フィールド

  * `I`: ストークス I モデル
  * `Q`: ストークス Q モデル
  * `U`: ストークス U モデル
  * `V`: ストークス V モデル
