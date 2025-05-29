```
MarginalizedStarAbsoluteRVLikelihood(
    (;epoch=5000.0,  rv=−6.54, σ_rv=1.30),
    (;epoch=5050.1,  rv=−3.33, σ_rv=1.09),
    (;epoch=5100.2,  rv=7.90,  σ_rv=.11),

    jitter=:jitter_1,
    instrument_name="inst name",
)
```

Represents a likelihood function of relative astometry between a host star and a secondary body. `:epoch` (mjd), `:rv` (m/s), and `:σ_rv` (m/s)  are all required. In addition to the example above, any Tables.jl compatible source can be provided.

The`jitter` parameters specify which variables should be read from the model for the      jitter of this instrument.

Unlike `StarAbsoluteRVLikelihood`, this version analytically marginalizes over the instrument RV zero point. This makes it faster in most cases. That said, if you have a specific prior you want to apply for the RV zero point, correlations between zero points, hierarchical models, etc, you should use `StarAbsoluteRVLikelihood`.

Additionally, a gaussian and trend fit are not supported with the analytically marginalization.
