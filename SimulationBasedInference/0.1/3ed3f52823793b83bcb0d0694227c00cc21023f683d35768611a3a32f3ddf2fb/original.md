```
SimulatorObservable(
    name::Symbol,
    obsfunc,
    t0::tType,
    tsave::AbstractVector{tType},
    output_shape_or_coords::Tuple;
    reducer=mean,
    samplerate=default_sample_rate(tsave),
) where {tType}
```

Constructs a `TimeSampled` observable which iteratively samples and stores outputs on each call to `observe!`.
