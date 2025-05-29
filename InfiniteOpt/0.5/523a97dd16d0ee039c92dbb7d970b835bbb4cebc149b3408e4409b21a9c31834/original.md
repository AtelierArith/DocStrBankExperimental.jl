```
set_domain_restrictions(cref::InfOptConstraintRef,
                     restrictions:DomainRestrictions{GeneralVariableRef};
                     [force::Bool = false])::Nothing
```

Specify a new [`DomainRestrictions`](@ref) object `restrictions` for the  constraint `cref`. Errors if `cref` already has restrictions and `force = false`.  Where possible it is recommended to use [`add_domain_restrictions`](@ref) instead.  

**Example**

```julia-repl
julia> set_domain_restrictions(cref, DomainRestrictions(t => [0, 2]))

julia> domain_restrictions(cref)
Subdomain restrictions (1): t ∈ [0, 2]
```
