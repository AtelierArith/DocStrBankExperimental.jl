```
concatenate!(X::LDLᵀ)
```

内部コンポーネントを連結して、`alpha`, `L`, `D` を `alpha, L, D = X` を通じて取得できるようにします。この関数は、`L = foldl(hcat, X.Ls)` および `D = foldl(dcat, Ds)` にほぼ相当し、ここで `dcat` は「対角連結」の擬似コードです。

これはやや安価な操作です。

参照: [`compress!`](@ref)
