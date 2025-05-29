```
print_dimacs(io = stdout, p)
```

Print the DIMACS format of `p`.

The `io` can be an `IO` or file path `String` to write to.

# Examples

```jldoctest
julia> @atomize print_dimacs(p ∧ q)
p cnf 2 2
1 0
2 0

julia> @atomize print_dimacs(p ↔ q)
p cnf 2 2
1 -2 0
-1 2 0
```
