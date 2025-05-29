```
add_domain_restrictions(cref::InfOptConstraintRef,
                     new_restrictions::DomainRestrictions{GeneralVariableRef}
                     )::Nothing
```

`cref`に追加のドメイン制約を追加し、`lower`から`upper`までのサブドメインに基づいて定義されるようにします。

```julia-repl
julia> add_domain_restrictions(cref, DomainRestrictions(t => [0, 2]))

julia> domain_restrictions(cref)
サブドメイン制約 (1): t ∈ [0, 2]
```
