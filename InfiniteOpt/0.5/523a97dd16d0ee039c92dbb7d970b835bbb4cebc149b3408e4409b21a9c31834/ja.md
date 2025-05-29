```
set_domain_restrictions(cref::InfOptConstraintRef,
                     restrictions:DomainRestrictions{GeneralVariableRef};
                     [force::Bool = false])::Nothing
```

制約 `cref` のために新しい [`DomainRestrictions`](@ref) オブジェクト `restrictions` を指定します。`cref` にすでに制限がある場合、`force = false` のときはエラーになります。可能な場合は、代わりに [`add_domain_restrictions`](@ref) を使用することをお勧めします。

**例**

```julia-repl
julia> set_domain_restrictions(cref, DomainRestrictions(t => [0, 2]))

julia> domain_restrictions(cref)
サブドメイン制限 (1): t ∈ [0, 2]
```
