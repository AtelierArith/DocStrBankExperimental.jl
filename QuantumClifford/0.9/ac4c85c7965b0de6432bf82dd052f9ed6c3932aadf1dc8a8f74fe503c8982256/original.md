For a given set S of Paulis that does not necessarily represent a state, return a set of Paulis S' that represents a state. S' is a superset of [commutified](@ref commutify) S. Additionally returns two arrays representing deletions needed to produce S. Based on [goodenough2024bipartiteentanglementnoisystabilizer](@cite)

By deleting the qubits in the first output array from S', taking the [`normalizer`](@ref) of S', then deleting the qubits in the second returned array from the [`normalizer`](@ref) of S', S is reproduced.

```jldoctest
julia> matroid_parent(T"XX")[1]
+ X_X
+ XX_
+ ZZZ

julia> matroid_parent(T"XX")[2]
3:3

julia> matroid_parent(T"XX")[3]
3:2
```
