```
OrdinalPatternEncoding <: Encoding
OrdinalPatternEncoding{m}(lt = ComplexityMeasures.isless_rand)
```

An encoding scheme that [`encode`](@ref)s length-`m` vectors into their permutation/ordinal patterns and then into the integers based on the Lehmer code. It is used by [`OrdinalPatterns`](@ref) and similar estimators, see that for a description of the outcome space.

The ordinal/permutation pattern of a vector `χ` is simply `sortperm(χ)`, which gives the indices that would sort `χ` in ascending order.

## Description

The Lehmer code, as implemented here, is a bijection between the set of `factorial(m)` possible permutations for a length-`m` sequence, and the integers `1, 2, …, factorial(m)`. The encoding step uses algorithm 1 in [Berger2019](@citet), which is highly optimized. The decoding step is much slower due to missing optimizations (pull requests welcomed!).

## Example

```jldoctest
julia> using ComplexityMeasures

julia> χ = [4.0, 1.0, 9.0];

julia> c = OrdinalPatternEncoding(3);

julia> i = encode(c, χ)
3

julia> decode(c, i)
3-element SVector{3, Int64} with indices SOneTo(3):
 2
 1
 3
```

If you want to encode something that is already a permutation pattern, then you can use the non-exported `permutation_to_integer` function.
