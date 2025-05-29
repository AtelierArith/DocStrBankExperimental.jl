```
JuMP.upper_bound(domain::AbstractInfiniteDomain)::Union{Real, Vector{<:Real}}
```

`domain`の上限を返します。存在する場合は、適切であればユーザー定義の無限ドメインに対して拡張されるべきです。`JuMP.has_upper_bound`が`false`を返す場合はエラーになります。拡張は`JuMP.has_upper_bound(domain)`と`JuMP.upper_bound(domain)`によって有効になります。

**例**

```jldoctest; setup = :(using InfiniteOpt, JuMP)
julia> domain = InfiniteDomain(0, 1);

julia> upper_bound(domain)
1.0
```
