```
CombinationEncoding <: Encoding
CombinationEncoding(encodings)
```

A `CombinationEncoding` takes multiple [`Encoding`](@ref)s and creates a combined encoding that can be used to encode inputs that are compatible with the given `encodings`.

## Encoding/decoding

When used with [`encode`](@ref), each [`Encoding`](@ref) in `encodings` returns integers in the set `1, 2, …, n_e`, where `n_e` is the total number of outcomes for a particular encoding. For `k` different encodings, we can thus construct the cartesian coordinate `(c₁, c₂, …, cₖ)` (`cᵢ ∈ 1, 2, …, n_i`), which can uniquely be identified by an integer. We can thus identify each unique *combined* encoding with a single integer.

When used with [`decode`](@ref), the integer symbol is converted to its corresponding cartesian coordinate, which is used to retrieve the decoded symbols for each of the encodings, and a tuple of the decoded symbols are returned.

The total number of outcomes is `prod(total_outcomes(e) for e in encodings)`.

## Examples

```julia
using ComplexityMeasures

# We want to encode the vector `x`.
x = [0.9, 0.2, 0.3]

# To do so, we will use a combination of first-difference encoding, amplitude encoding,
# and ordinal pattern encoding.

encodings = (
    RelativeFirstDifferenceEncoding(0, 1; n = 2),
    RelativeMeanEncoding(0, 1; n = 5),
    OrdinalPatternEncoding(3) # x is a three-element vector
    )
c = CombinationEncoding(encodings)

# Encode `x` as integer
ω = encode(c, x)

# Decode symbol (into a vector of decodings, one for each encodings `e ∈ encodings`).
# In this particular case, the first two element will be left-bin edges, and
# the last element will be the decoded ordinal pattern (indices that would sort `x`).
d = decode(c, ω)
```
