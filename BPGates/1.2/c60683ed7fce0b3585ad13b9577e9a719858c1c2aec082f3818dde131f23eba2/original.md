Bell preserving gate performing one of 4 possible "Pauli permutations" on a single Bell pair.

Equivalent to applying a Pauli gate to Alice's side of the Bell pair.

The first argument, `pidx`, specifies the permutation (between 1 and 4). The second argument, `sidx` indicates which Bell pair is acted on.

```jldoctest
julia> BellPauliPermutation(1,1)*BellState(1) |> Stabilizer
+ XX
+ ZZ

julia> BellPauliPermutation(2,1)*BellState(1) |> Stabilizer
+ XX
- ZZ

julia> BellPauliPermutation(3,1)*BellState(1) |> Stabilizer
- XX
+ ZZ

julia> BellPauliPermutation(4,1)*BellState(1) |> Stabilizer
- XX
- ZZ
```
