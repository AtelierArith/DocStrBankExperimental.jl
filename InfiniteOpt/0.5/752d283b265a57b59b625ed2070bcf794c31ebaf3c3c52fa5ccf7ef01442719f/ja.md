```
JuMP.has_upper_bound(domain::AbstractInfiniteDomain)::Bool
```

`domain` に対して決定可能な上限があるかどうかを示す `Bool` を返します。これはユーザー定義の無限ドメインに対して拡張されるべきです。認識されないドメインタイプに対してはデフォルトで `false` になります。

**例**

```jldoctest; setup = :(using InfiniteOpt, JuMP)
julia> domain = InfiniteDomain(0, 1);

julia> has_upper_bound(domain)
true
```
