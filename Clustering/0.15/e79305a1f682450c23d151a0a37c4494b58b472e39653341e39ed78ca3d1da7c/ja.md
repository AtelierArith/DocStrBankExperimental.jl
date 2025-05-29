```
kmeans!(X, centers; [kwargs...]) -> KmeansResult
```

現在のクラスタ `centers` ($d×k$ 行列、ここで $d$ は次元、$k$ はセントロイドの数) を $d×n$ データ行列 `X` を使用して更新します（`X` の各列は $d$ 次元のデータポイントです）。

オプションの `kwargs` の説明については [`kmeans`](@ref) を参照してください。
