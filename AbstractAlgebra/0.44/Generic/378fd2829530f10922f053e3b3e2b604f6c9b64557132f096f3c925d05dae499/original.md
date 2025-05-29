```
dim(Y::YoungTableau) -> BigInt
```

Return the dimension (using hook-length formula) of the irreducible representation of permutation group $S_n$ associated the partition `Y.part`.

Since the computation overflows easily `BigInt` is returned. You may perform the computation of the dimension in different type by calling `dim(Int, Y)`.

# Examples

```jldoctest
julia> dim(YoungTableau([4,3,1]))
70

julia> dim(YoungTableau([3,1])) # the regular representation of S_4
3
```
