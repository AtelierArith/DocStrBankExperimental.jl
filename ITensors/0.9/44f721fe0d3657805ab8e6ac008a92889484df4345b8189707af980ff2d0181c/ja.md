```
ITensor([::Type{ElT} = Float64, ]inds)
ITensor([::Type{ElT} = Float64, ]inds::Index...)
```

インデックス `inds` と要素型 `ElT` を持つゼロで満たされた ITensor を構築します。要素型が指定されていない場合、デフォルトは `Float64` です。

ストレージは `NDTensors.Dense` 型になります。

# 例

```julia
i = Index(2,"index_i")
j = Index(4,"index_j")
k = Index(3,"index_k")

A = ITensor(i,j)
B = ITensor(ComplexF64,k,j)
```
