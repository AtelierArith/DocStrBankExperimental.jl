```
parity(g::Perm)
```

Return the parity of the given permutation, i.e. the parity of the number of transpositions in any decomposition of `g` into transpositions.

`parity` returns $1$ if the number is odd and $0$ otherwise. `parity` uses cycle decomposition of `g` if already available, but will not compute it on demand. Since cycle structure is cached in `g` you may call `cycles(g)` before calling `parity`.

# Examples

```jldoctest
julia> g = Perm([3,4,1,2,5])
(1,3)(2,4)

julia> parity(g)
0

julia> g = Perm([3,4,5,2,1,6])
(1,3,5)(2,4)

julia> parity(g)
1
```
