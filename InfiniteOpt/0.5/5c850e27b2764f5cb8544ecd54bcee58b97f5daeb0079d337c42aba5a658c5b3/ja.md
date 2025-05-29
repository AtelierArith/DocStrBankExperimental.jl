```
infinite_domain(pref::DependentParameterRef)::InfiniteScalarDomain
```

特定の無限依存パラメータ `pref` に関連する無限ドメインを返します。エラーが発生するのは、基になる [`DependentParameters`](@ref) オブジェクトが [`CollectionDomain`](@ref) を使用していない場合です。

**例**

```julia-repl
julia> infinite_domain(x[1])
[-1, 1]
```
