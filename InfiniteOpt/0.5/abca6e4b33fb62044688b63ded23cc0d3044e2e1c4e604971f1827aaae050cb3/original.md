```
delete_domain_restrictions(cref::InfOptConstraintRef)::Nothing
```

Delete all the domain restrictions of the constraint `cref`. Note any restrictions that are needed for finite variables inside in `cref` will be unaffected.

**Example**

```julia-repl
julia> @constraint(model, c1, y <= 42, DomainRestrictions(x => 0))
c1 : y(x) ≤ 42, ∀ x[1] = 0, x[2] = 0

julia> delete_domain_restrictions(c1)

julia> c1
c1 : y(x) ≤ 42, ∀ x[1] ∈ [-1, 1], x[2] ∈ [-1, 1]
```
