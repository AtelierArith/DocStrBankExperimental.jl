```
wasserstein(μ, ν; metric=Euclidean(), p=Val(1), kwargs...)
```

測度 `μ` と `ν` の間の `metric` に関する `p`-ワッサースタイン距離を計算します。

`p` の順序は、`Real` 型のスカラーとして提供することも、値型 `Val(p)` のパラメータとして提供することもできます。`metric` と `p` の特定の組み合わせ、例えば `metric=Euclidean()` と `p=Val(2)` の場合、`p` を値型として指定すると計算がより効率的になります。残りのキーワード引数は [`ot_cost`](@ref) に渡されます。

参照: [`squared2wasserstein`](@ref), [`ot_cost`](@ref)
