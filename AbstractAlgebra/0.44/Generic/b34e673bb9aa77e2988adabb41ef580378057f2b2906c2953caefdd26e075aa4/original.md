```
perm"..."
```

String macro to parse disjoint cycles into `Perm{Int}`.

Strings for the output of GAP could be copied directly into `perm"..."`. Cycles of length $1$ are not necessary, but can be included. A permutation of the minimal support is constructed, i.e. the maximal $n$ in the decomposition determines the parent group $S_n$.

# Examples

```jldoctest
julia> p = perm"(1,3)(2,4)"
(1,3)(2,4)

julia> typeof(p)
Perm{Int64}

julia> parent(p) == SymmetricGroup(4)
true

julia> p = perm"(1,3)(2,4)(10)"
(1,3)(2,4)

julia> parent(p) == SymmetricGroup(10)
true
```
