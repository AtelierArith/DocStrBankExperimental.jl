```
transmute(A, perm⁺)
transmute(A, Val(perm⁺))
```

Gives a result `== TransmutedDimsArray(A, perm⁺)`, but:

  * When `A` is a `PermutedDimsArray`, `Transpose{<:Number}`, `Adjoint{<:Real}`, or `Diagonal`, it will un-wrap this, and adjust `perm⁺` to work directly on `parent(A)`.
  * When the permutation simply inserts or removes a trivial dimension, it prefers to `reshape` instead of wrapping. This is controlled by `may_reshape(::Type)`, by default true for `DenseArray`s and `ReshapedArray`s.
  * When possible, it prefers to create a `Transpose` or `Diagonal`, instead of a `TransmutedDimsArray`.
  * If the permutation is wrapped in `Val`, then computing its inverse (and performing sanity checks) is always done at compile-time.

# Examples

```jldoctest; setup=:(using TransmuteDims, Random; Random.seed!(42);)
julia> A = transpose(rand(Int8, 4, 2))
2×4 transpose(::Matrix{Int8}) with eltype Int8:
 115    99  0  57
  88  -105  3  76

julia> B = transmute(A, (3,2,1))  # unwraps transpose, and then reshapes
1×4×2 Array{Int8, 3}:
[:, :, 1] =
 115  99  0  57

[:, :, 2] =
 88  -105  3  76

julia> B == TransmutedDimsArray(A, (0,2,1))  # same values, different type
true

julia> transmute(A, (2,2,0,1))
4×4×1×2 transmute(::Matrix{Int8}, (1, 1, 0, 2)) with eltype Int8:
[:, :, 1, 1] =
 115   ⋅  ⋅   ⋅
   ⋅  99  ⋅   ⋅
   ⋅   ⋅  0   ⋅
   ⋅   ⋅  ⋅  57

[:, :, 1, 2] =
 88     ⋅  ⋅   ⋅
  ⋅  -105  ⋅   ⋅
  ⋅     ⋅  3   ⋅
  ⋅     ⋅  ⋅  76

julia> ans == transmute(B, (2,2,1,3))
true

julia> TransmuteDims.may_reshape(typeof(A))  # avoids reshaping wrappers
false

julia> TransmuteDims.may_reshape(typeof(B))
true

julia> transmute(('α', "β", :γ), (2,1))  # accepts tuples, too
1×3 transmute(TupleVector(::Tuple{Char, String, Symbol}), (0, 1)) with eltype Any:
 'α'  "β"  :γ
```
