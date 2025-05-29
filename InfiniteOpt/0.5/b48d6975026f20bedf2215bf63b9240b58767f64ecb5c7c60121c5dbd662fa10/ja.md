```
set_infinite_domain(prefs::AbstractArray{<:DependentParameterRef},
                 domain::InfiniteArrayDomain)::Nothing
```

依存する無限パラメータ `prefs` の多次元無限ドメインを `domain` に指定します。これにより、基盤となる [`DependentParameters`](@ref) オブジェクトに含まれるすべてのサポートがリセット/削除されます。すべての依存する無限パラメータが含まれていない場合や、いずれかが測定に使用されている場合はエラーになります。

**例**

```julia-repl
julia> set_infinite_domain(x, CollectionDomain([IntervalDomain(0, 1), IntervalDomain(0, 2)]))
```
