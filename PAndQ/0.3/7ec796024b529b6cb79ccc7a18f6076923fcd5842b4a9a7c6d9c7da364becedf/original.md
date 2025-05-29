```
atoms(p)
```

Return an iterator of each atomic proposition contained in `p`.

# Examples

```jldoctest
julia> @atomize collect(atoms(p ∧ q))
2-element Vector{PAndQ.Variable}:
 p
 q
```
