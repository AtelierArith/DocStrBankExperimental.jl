```
JuMP.lower_bound(domain::AbstractInfiniteDomain)::Union{Real, Vector{<:Real}}
```

`domain`の下限が存在する場合はそれを返します。適切であれば、ユーザー定義の無限ドメインに対して拡張する必要があります。`JuMP.has_lower_bound`が`false`を返す場合はエラーになります。拡張は`JuMP.has_lower_bound(domain)`と`JuMP.lower_bound(domain)`によって有効になります。

**例**

```jldoctest; setup = :(using InfiniteOpt, JuMP)
julia> domain = InfiniteDomain(0, 1);

julia> lower_bound(domain)
0.0
```
