```
JuMP.set_upper_bound(domain::AbstractInfiniteDomain,
                     upper::Real)::AbstractInfiniteDomain
```

`domain`の上限を設定して返します。この操作が意味を持つ場合に限ります。この操作をサポートしていない型の`domain`や拡張されていない型の場合はエラーになります。ユーザー定義のドメイン型は、適切であればこれを拡張する必要があります。

**例**

```jldoctest; setup = :(using InfiniteOpt, JuMP)
julia> domain = InfiniteDomain(0, 1);

julia> set_upper_bound(domain, 0.5)
[0, 0.5]
```
