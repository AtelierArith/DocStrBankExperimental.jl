For a not-necessarily commutative set of Paulis S, computed S', the [non-commutative canonical form](@ref canonicalize_noncomm) of of S. For each pair Aₖ, Bₖ of anticommutative Paulis in S', add a qubit to each Pauli in the set: X to Aₖ, Z to Bₖ, and I to each other operator to produce S'', a fully commutative set. Return S'' as well as a list of the indices of the added qubits.

The returned object is a Stabilizer that is also useful for the [`matroid_parent`](@ref) function.

```jldoctest
julia> commutify(T"XX XZ XY")[1]
+ XXX
+ X__
+ XZZ

julia> commutify(T"XX XZ XY")[2]
3:3
```
