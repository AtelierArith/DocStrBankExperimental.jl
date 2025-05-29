```
@mix_proposals weight1 propose1 weight2 propose2 ...
```

Macro to generate a proposal function that randomly selects among the provided functions according to the provided probability weights. For use with [`LocalSampler`](@ref).

# Example

```julia
# A proposal function that proposes a spin flip 40% of the time, and a
# Gaussian perturbation 60% of the time.
@mix_proposals 0.4 propose_flip 0.6 propose_delta(0.2)
```
