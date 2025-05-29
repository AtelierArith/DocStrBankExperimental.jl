```
JuMP.set_lower_bound(domain::AbstractInfiniteDomain,
                     lower::Union{Real, Vector{<:Real}})::AbstractInfiniteDomain
```

`domain`の下限を設定して返します。この操作が意味を持つ場合に限ります。`domain`の型がこの操作をサポートしていない場合や拡張されていない場合はエラーが発生します。ユーザー定義のドメイン型は、適切であればこれを拡張する必要があります。

**例**

```jldoctest; setup = :(using InfiniteOpt, JuMP)
julia> domain = InfiniteDomain(0, 1);

julia> set_lower_bound(domain, 0.5)
[0.5, 1]
```
