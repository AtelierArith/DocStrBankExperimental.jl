```
prod(strategy, left, right)
```

`prod` 関数は、同じ変数に対する二つの確率分布（または他の任意のオブジェクト）の積を求めるために使用されます（例：𝓝(x|μ*1, σ*1) × 𝓝(x|μ*2, σ*2)）。`prod` 関数には、`ClosedProd`、`GenericProd`、または `PreserveTypeProd` など、複数の戦略があります。

参照： [`default_prod_rule`](@ref), [`ClosedProd`](@ref), [`PreserveTypeProd`](@ref), [`GenericProd`](@ref)
