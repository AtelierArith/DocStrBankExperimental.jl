```
random_itensor([rng=Random.default_rng()], [ElT=Float64], inds)
random_itensor([rng=Random.default_rng()], [ElT=Float64], inds::Index...)
```

タイプ `ElT` とインデックス `inds` を持つ ITensor を構築します。その要素は正規分布に従うランダムな数値です。要素の型が指定されていない場合、デフォルトは `Float64` です。

# 例

```julia
i = Index(2,"index_i")
j = Index(4,"index_j")
k = Index(3,"index_k")

A = random_itensor(i,j)
B = random_itensor(ComplexF64,undef,k,j)
```
