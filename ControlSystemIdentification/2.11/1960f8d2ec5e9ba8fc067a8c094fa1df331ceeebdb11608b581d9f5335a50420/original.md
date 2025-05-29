```
specplot(d::IdData, args...; kwargs...)
```

Plot a spectrogram of the input and output timeseries. See also [`welchplot`](@ref).

Additional arguments are passed along to `DSP.spectrogram`.
