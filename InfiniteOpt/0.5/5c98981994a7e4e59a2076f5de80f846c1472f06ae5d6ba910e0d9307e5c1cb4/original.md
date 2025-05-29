```
add_domain_restrictions(cref::InfOptConstraintRef,
                     new_restrictions::DomainRestrictions{GeneralVariableRef}
                     )::Nothing
```

Add additional domain restrictions to `cref` such that it is defined over the sub-domain based on `pref` from `lower` to `upper`.

```julia-repl
julia> add_domain_restrictions(cref, DomainRestrictions(t => [0, 2]))

julia> domain_restrictions(cref)
Subdomain restrictions (1): t ∈ [0, 2]
```
