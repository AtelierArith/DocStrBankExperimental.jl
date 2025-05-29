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

`observe!`を呼び出すたびに出力を反復的にサンプリングして保存する`TimeSampled`可観測量を構築します。
