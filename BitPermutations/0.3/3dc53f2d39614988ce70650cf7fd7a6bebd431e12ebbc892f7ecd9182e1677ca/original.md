```
BitPermutation{T}([backend_type], p::AbstractVector{Int}; [...])
```

Construct a `BitPermutation{T}` from permutation vector `p`. The backend that actually performs the permutation can be optionally specified by providing a `backend_type` (`<:PermutationBackend`). It defaults to the following:

  * if AVX-512 instrinsics are available, `AVXCopyGather` is chosen for `T<:Union{UInt16,UInt32,UInt64}`;
  * if BMI2 instrinsics are available, `GRPNetwork` is chosen for `T<:Union{UInt32,UInt64}`;
  * In all other cases, `BenesNetwork` is used.

Extra keyword arguments get passed to the backend.

See also: [`BenesNetwork`](@ref), [`GRPNetwork`](@ref), [`AVXCopyGather`](@ref).
