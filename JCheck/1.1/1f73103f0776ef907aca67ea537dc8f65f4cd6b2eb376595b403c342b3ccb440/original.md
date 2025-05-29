```
generate([rng=GLOBAL_RNG], T, n)
```

Sample `n` random instances of type `T`.

# Arguments

  * `rng::AbstractRNG`: random number generator to use
  * `T::Type`: type of the instances
  * `n::Int`: number of realizations to sample

# Default generators

`generate` methods for the following types are shipped with this package:

  * Subtypes of `AbstractFloat`
  * Subtypes of `Integer` except `BigInt`
  * `Complex{T <: Real}`
  * `String`
  * `Char`
  * `Array{T, N}`
  * `BitArray{N}`
  * `SquareMatrix{T}`.
  * Any [special matrix](https://docs.julialang.org/en/v1/stdlib/LinearAlgebra/#Special-matrices) implemented by Julia's LinearAlgebra module
  * `Union{T...}`
  * `UnitRange{T}`, `StepRange{T, T}`

In the previous list, `T` represents any type for which a `generate` method is implemented.

# Special Matrices (LinearAlgebra)

  * Generators are implemented for `<...>Triangular{T}` as well as `<...>Triangular{T, S}`. In the first case, `S` defaults to `SquareMatrix{T}`. The exact same thing is true for `UpperHessenberg`.
  * Same idea for `<...>diagonal{T, V}` with `V` defaulting to `Vector{T}`.
  * Generators are only implemented for `Symmetric{T, S}` and `Hermitian{T, S}` right now. Most of the time, you will want to specify `S` = `SquareMatrix{T}`.

# Arrays & Strings

General purpose generators for arrays and strings are a little bit tricky to implement given that a length for each sampled element must be specified. The following choices have been made for the default generators shipped with this package:

  * `String`: The length of each string is approximately exponentially distributed with mean 64.
  * `Array{T, N}`: The length of each dimension of a given array is approximately exponentially distributed with mean 24 ÷ N + 1 (in a low effort attempt to keep the number of entries manageable).

If this is not appropriate for your needs, don't hesitate to reimplement `generate`.

# Implementation

When implementing `generate` for your type `T` keep the following in mind:

  * Your method should return a `Vector{T}`.
  * It is not necessary to write `generate(T, n)` or `generate([rng, ]Array{T, N}, n) where N`; this is handled automatically. You only need to implement `generate(::AbstractRNG, ::Type{T}, ::Int)`.
  * Consider implementing [`specialcases`](@ref) and [`shrink`](@ref) for `T` as well.

# Examples

```jldoctest
using Random: Xoshiro

rng = Xoshiro(42)

generate(rng, Float32, 10)

# output

10-element Vector{Float32}:
 -1.5388016f7
 -5.3113024f-19
 -1.3960648f35
  1.5957566f31
 -4.381218f26
  2.380078f35
  3.878954f9
 -1.1950524f-7
  7.525897f24
 -3.1891005f-12
```
