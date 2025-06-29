```
PermutedDimsQuasiArray(A, perm) -> B
```

Given an AbstractQuasiArray `A`, create a view `B` such that the dimensions appear to be permuted. Similar to `permutedims`, except that no copying occurs (`B` shares storage with `A`).

See also: [`permutedims`](@ref).

# Examples

```jldoctest
julia> A = rand(3,5,4);

julia> B = PermutedDimsQuasiArray(A, (3,1,2));

julia> size(B)
(4, 3, 5)

julia> B[3,1,2] == A[1,2,3]
true
```
