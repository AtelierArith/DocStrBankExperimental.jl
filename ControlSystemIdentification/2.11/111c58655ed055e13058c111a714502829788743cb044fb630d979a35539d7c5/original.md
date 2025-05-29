```
welchplot(d::IdData, args...; kwargs...)
```

Plot a Wlch peridogram of the input and output timeseries. See also [`specplot`](@ref).

Additional arguments are passed along to `DSP.welch_pgram`.
