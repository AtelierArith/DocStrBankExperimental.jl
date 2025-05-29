```
has_domain_restrictions(cref::InfOptConstraintRef)::Bool
```

Return a `Bool` indicating if `cref` is limited to a sub-domain as defined by a [`DomainRestrictions`](@ref) object.

**Example**

```julia-repl
julia> has_domain_restrictions(cref)
true
```
