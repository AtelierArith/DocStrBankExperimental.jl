```julia
struct CustomAlgorithmTune{T<:ModelWrappers.Tagged, B<:BaytesCore.UpdateBool} <: BaytesCore.AbstractTune
```

カスタムアルゴリズム全体で使用される情報を格納します。

# フィールド

  * `tagged::ModelWrappers.Tagged`: アルゴリズムルーチンのためのタグ付きパラメータ
  * `generated::BaytesCore.UpdateBool`: サンプリング中に生成された量を生成する必要があるかどうかのブール値
  * `iter::BaytesCore.Iterator`: 現在のイテレーション番号
