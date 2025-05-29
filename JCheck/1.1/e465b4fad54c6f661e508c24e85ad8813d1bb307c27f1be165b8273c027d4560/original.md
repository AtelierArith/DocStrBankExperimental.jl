```
specialcases(T)
```

Non-random inputs that are always checked by [`@quickcheck`](@ref).

# Arguments

  * `T::Type`: type of the inputs

# Implementation

  * Your method should return a `Vector{T}`.
  * Useless without a [`generate`](@ref) method for `T`.
  * Be mindful of combinatoric explosion! [`@quickcheck`](@ref) generate an input for each element of the Cartesian product of the special cases of every argument of the predicates it is trying to falsify. Only include special cases that are *truly* special.

# Examples

```jldoctest
julia> specialcases(Int)
4-element Vector{Int64}:
                    0
                    1
 -9223372036854775808
  9223372036854775807

julia> specialcases(Float64)
4-element Vector{Float64}:
   0.0
   1.0
 -Inf
  Inf
```
