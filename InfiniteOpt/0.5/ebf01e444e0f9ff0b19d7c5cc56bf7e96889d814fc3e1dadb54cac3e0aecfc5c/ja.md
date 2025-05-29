```
set_infinite_domain(pref::IndependentParameterRef,
                 domain::InfiniteScalarDomain)::Nothing
```

`pref` の無限ドメインを別の `InfiniteScalarDomain` でリセットします。`pref` がいくつかの測定に使用されている場合、エラーが発生します。

**例**

```julia-repl
julia> set_infinite_domain(t, IntervalDomain(0, 2))

julia> infinite_domain(t)
[0, 2]
```
