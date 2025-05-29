```
parity(p)
```

Compute the parity of a permutation `p` using the [`levicivita`](@ref) function, permitting calls such as `iseven(parity(p))`. If `p` is not a permutation then an error is thrown.

# Examples

```jldoctest
julia> parity([1, 2, 3])
0

julia> parity([3, 2, 1])
1

julia> parity([1, 1, 1])
ERROR: ArgumentError: Not a permutation
[...]

julia> parity((collect(1:100)))
0
```
