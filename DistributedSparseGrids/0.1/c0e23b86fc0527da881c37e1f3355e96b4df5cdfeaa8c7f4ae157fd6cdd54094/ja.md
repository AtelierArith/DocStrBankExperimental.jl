```
CollocationPoint{N,CT} <: AbstractCollocationPoint{N,CT}
```

コレクションポイント。

# フィールド

`i_multi::SVector{N,Int}` : このベクトルの i 番目のアイテムは、i 番目の次元におけるコレクションポイントのレベルを表します。 `pt_idx::SVector{N,Int}` : このベクトルの i 番目のアイテムは、i 番目の次元におけるコレクションポイントのポイントインデックスを表します。 `coords::SVector{N,CT}` : コレクションポイントの座標。 `interv::SVector{N,SVector{2,CT}}` : ベクトルの i 番目のアイテムは、i 番目の次元における関連する基底関数の非ゼロ区間を定義します。
