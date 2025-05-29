```
Signature(positive::Int, negative::Int = 0, degenerate::Int = 0)
Signature(str::AbstractString) # Signature("++-𝟎")
```

ユークリッド空間または擬似ユークリッド空間の署名。

この署名は、最初の `P` 基底ベクトルが 1 の二乗を持ち、次の `N` が -1 の二乗を持ち、次の `D` が 0 の二乗を持つメトリックを持つ空間をエンコードします。メトリックは、2つの異なる基底ベクトルの間でゼロに評価されます。
