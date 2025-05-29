```
kmedoids!(dist::AbstractMatrix, medoids::Vector{Int};
          [kwargs...]) -> KmedoidsResult
```

現在のクラスタ `medoids` を `dist` 行列を使用して更新します。

返される `KmedoidsResult` の `medoids` フィールドは、`medoids` 引数と同じ配列を指します。

オプションの `kwargs` の説明については [`kmedoids`](@ref) を参照してください。
