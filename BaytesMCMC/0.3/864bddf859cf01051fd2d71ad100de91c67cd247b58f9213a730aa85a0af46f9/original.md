```julia
calculate_logprob2(_, is_doubling, ω₁, ω₂, ω)

```

Calculate the log probability if selecting the subtree corresponding to `ω₂`. Being the log of a probability, it is always `≤ 0`, but implementations are allowed to return and accept values `> 0` and treat them as `0`. When `is_doubling`, the tree corresponding to `ω₂` was obtained from a doubling step (this can be relevant eg for biased progressive sampling). The value `ω = logaddexp(ω₁, ω₂)` is provided for avoiding redundant calculations. See [`biased_progressive_logprob2`](@ref) for an implementation.

# Examples

```julia

```
