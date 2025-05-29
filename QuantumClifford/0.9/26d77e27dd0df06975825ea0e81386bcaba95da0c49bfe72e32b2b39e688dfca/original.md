For a given set of Paulis (in the form of a `Tableau`), return the subset of Paulis that commute with all Paulis in set.

```jldoctest
julia> centralizer(T"XX ZZ _Z")
+ ZZ
```
