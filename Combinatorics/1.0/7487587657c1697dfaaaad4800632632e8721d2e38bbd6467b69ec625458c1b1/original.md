```
levicivita(p)
```

Compute the Levi-Civita symbol of a permutation `p`. Returns 1 if the permutation is even, -1 if it is odd, and 0 otherwise.

The parity is computed by using the fact that a permutation is odd if and only if the number of even-length cycles is odd.

# Examples

```jldoctest
julia> levicivita([1, 2, 3])
1

julia> levicivita([3, 2, 1])
-1

julia> levicivita([1, 1, 1])
0

julia> levicivita(collect(1:100))
1

julia> levicivita(ones(Int, 100))
0
```
