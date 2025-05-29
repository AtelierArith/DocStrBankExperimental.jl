```
domain_restrictions(cref::InfOptConstraintRef)::DomainRestrictions{GeneralVariableRef}
```

Return the [`DomainRestrictions`](@ref) object associated with the constraint `cref`.

**Example**

```julia-repl
julia> domain_restrictions(cref)
Subdomain restrictions (1): t ∈ [0, 2]
```
