```
print_proposition(io, p)
```

Print the given proposition with the `IOContext` that `:root => false`.

Should be called from [`print_expression`](@ref Interface.print_expression).

# Examples

```jldoctest
julia> @atomize print_proposition(stdout, ¬p)
¬p

julia> @atomize print_proposition(stdout, p ∧ q)
(p ∧ q)
```
