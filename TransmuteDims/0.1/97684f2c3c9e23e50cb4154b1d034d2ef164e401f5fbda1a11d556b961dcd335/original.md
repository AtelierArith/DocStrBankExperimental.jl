```
TransmutedDimsArray(A, perm⁺)
```

This is just like `PermutedDimsArray`, except that `perm⁺` need not be a permutation:

  * Where it contains `0`, this inserts a trivial dimension into the output, size 1. Anything outside `1:ndims(A)` is treated like `0` – fitting with `size(A,99) == 1`, but also allowing `nothing`.
  * Any number omitted from `perm⁺` is a dimension to be dropped, which must be of size 1.
  * When a number appears twice in `perm⁺`, the result works like `Diagonal` in those dimensions.

By calling the type directly you get the simplest constructor. Calling instead [`transmute(A, perm⁺)`](@ref) gives one which un-wraps nested objects, picks simpler alternatives, etc. And [`transmutedims(A, perm⁺)`](@ref) is the eager version.

# Examples

```jldoctest; setup=:(using TransmuteDims)
julia> TransmutedDimsArray('a':'e', (2,1))  # like transpose
1×5 transmute(::StepRange{Char, Int64}, (0, 1)) with eltype Char:
 'a'  'b'  'c'  'd'  'e'

julia> TransmutedDimsArray('a':'e', (nothing, 1, nothing))  # two trivial dimensions
1×5×1 transmute(::StepRange{Char, Int64}, (0, 1, 0)) with eltype Char:
[:, :, 1] =
 'a'  'b'  'c'  'd'  'e'

julia> A = rand(10, 20, 30);

julia> B = TransmutedDimsArray(A, (3,0,1,2));  # like reshape + permute

julia> size(B)
(30, 1, 10, 20)

julia> B[3,1,1,2] == A[1,2,3] == A[1,2,3,1]  # implicit trailing dimensions
true

julia> B == TransmutedDimsArray(A, (3,4,1,2)) == permutedims(A[:,:,:,:], (3,4,1,2))
true

julia> TransmutedDimsArray(reshape(1:6,3,2), (1,1,2))  # generalised Diagonal
3×3×2 transmute(reshape(::UnitRange{Int64}, 3, 2), (1, 1, 2)) with eltype Int64:
[:, :, 1] =
 1  ⋅  ⋅
 ⋅  2  ⋅
 ⋅  ⋅  3

[:, :, 2] =
 4  ⋅  ⋅
 ⋅  5  ⋅
 ⋅  ⋅  6
```
