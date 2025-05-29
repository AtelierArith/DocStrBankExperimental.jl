Return all Pauli operators with the same number of qubits as the given `Tableau` `t` that commute with all operators in `t`.

```jldoctest
julia> normalizer(T"X")
+ _
+ X
```
