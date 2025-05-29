```julia
struct OptimTune{T<:ModelWrappers.Tagged, K, B<:BaytesCore.UpdateBool} <: BaytesCore.AbstractTune
```

最適化アルゴリズム全体で使用される情報を格納します。

# フィールド

  * `tagged::ModelWrappers.Tagged`: 最適化ルーチンのためのタグ付きパラメータ
  * `kernel::Any`: 個々の最適化者のための調整引数
  * `generated::BaytesCore.UpdateBool`: サンプリング中に生成された量を生成する必要があるかどうかのブール値
  * `iter::BaytesCore.Iterator`: 現在のイテレーション番号
