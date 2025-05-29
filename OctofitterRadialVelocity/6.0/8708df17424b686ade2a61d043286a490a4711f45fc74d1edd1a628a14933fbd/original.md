StarAbsoluteRVLikelihood(         (;epoch=5000.0,  rv=−6.54, σ*rv=1.30),         (;epoch=5050.1,  rv=−3.33, σ*rv=1.09),         (;epoch=5100.2,  rv=7.90,  σ_rv=.11),

```
    offset=:offset_1,
    jitter=:jitter_1,
    instrument_name="inst name",

    # Optional:
    trend_function=(θ_system, epoch)->0.,
    gaussian_process=nothing
)
```

Represents a likelihood function of relative astometry between a host star and a secondary body. `:epoch` (mjd), `:rv` (m/s), and `:σ_rv` (m/s)  are all required.

The `offset` and `jitter` parameters specify which variables should be read from the model for the  RV zero-point and jitter of this instrument.

In addition to the example above, any Tables.jl compatible source can be provided.
