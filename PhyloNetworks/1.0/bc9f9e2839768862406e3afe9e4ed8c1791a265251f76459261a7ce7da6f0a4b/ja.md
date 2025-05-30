```
nj(D::DataFrame; force_nonnegative_edges::Bool=false)
```

距離行列から隣接結合によって木を構築します。ここで、`D`は距離行列の`DataFrame`であり、分類群の名前はデータフレームのヘッダーから取得されます。行は列と同じ順序で木の先端に対応していると仮定されます。`force_nonnegative_edges`が`true`の場合、負のエッジ長は0.0に変更されます（メッセージ付き）。

アルゴリズムについては、[Satou & Nei 1987](https://doi.org/10.1093/oxfordjournals.molbev.a040454)を参照してください。

行列を入力として使用する場合は、[`nj!`](@ref)を参照してください。
