```
externalsampler(sampler::AbstractSampler; adtype=AutoForwardDiff(), unconstrained=true)
```

Wrap a sampler so it can be used as an inference algorithm.

# Arguments

  * `sampler::AbstractSampler`: The sampler to wrap.

# Keyword Arguments

  * `adtype::ADTypes.AbstractADType=ADTypes.AutoForwardDiff()`: The automatic differentiation (AD) backend to use.
  * `unconstrained::Bool=true`: Whether the sampler requires unconstrained space.
