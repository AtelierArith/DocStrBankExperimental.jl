```
bat_sample(
    target::BAT.AnySampleable,
    [algorithm::BAT.AbstractSamplingAlgorithm],
    [context::BATContext]
)::DensitySampleVector
```

Draw samples from `target` using `algorithm`.

Depending on sampling algorithm, the samples may be independent or correlated (e.g. when using MCMC).

Returns a NamedTuple of the shape

```julia
(result = X::DensitySampleVector, ...)
```

Result properties not listed here are algorithm-specific and are not part of the stable public API.

!!! note
    Do not add add methods to `bat_sample`, add methods to `bat_sample_impl` instead.

