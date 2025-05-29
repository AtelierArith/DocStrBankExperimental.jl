```
set_infinite_domain(pref::DependentParameterRef,
                 domain::InfiniteScalarDomain)::Nothing
```

依存する無限パラメータ `pref` のスカラー無限ドメインを `domain` に指定します。`pref` が [`CollectionDomain`](@ref) の一部でない場合、エラーがスローされます。この操作は、基になる [`DependentParameters`](@ref) オブジェクトに含まれるすべてのサポートをリセット/削除します。また、`pref` が測定に使用されている場合もエラーが発生します。

**例**

```julia-repl
julia> set_infinite_domain(x[1], IntervalDomain(0, 2))

julia> infinite_domain(x[1])
[0, 2]
```
