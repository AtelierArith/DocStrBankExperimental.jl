```julia
bigram(
    state::QuantumClifford.AbstractStabilizer;
    clip
) -> Matrix{Int64}

```

Get the bigram of a tableau.

It is the list of endpoints of a tableau in the clipped gauge.

If `clip=true` (the default) the tableau is converted to the clipped gauge in-place before calculating the bigram. Otherwise, the clip gauge conversion is skipped (for cases where the input is already known to be in the correct gauge).

Introduced in [nahum2017quantum](@cite), with a more detailed explanation of the algorithm in [li2019measurement](@cite) and [gullans2021quantum](@cite).

See also: [`canonicalize_clip!`](@ref)
