```
cutree(::PopData, hcres::Hclust; krange::UnitRange{Int64}, height::Union{Int64, Nothing} = nothing)
cutree(::PopData, hcres::Hclust; krange::Vector{Int64}, height::Union{Int64, Nothing} = nothing)
```

`Clustering.cutree` メソッド (Clustering.jl から) の拡張で、`hclust()` の出力から `krange` にわたるクラスタ割り当てを実行します。サンプル名と `krange` の各 k に対応する割り当ての列を含む `DataFrame` を返します。`PopData` オブジェクトはサンプル名を取得するためだけに使用されます。

**キーワード引数**

  * `krange`: 希望するクラスタの数をベクトル (例: `[2,4,5]`) または範囲 (`2:5`) として指定します
  * `h::Integer`: 木を切る高さ (オプション)
