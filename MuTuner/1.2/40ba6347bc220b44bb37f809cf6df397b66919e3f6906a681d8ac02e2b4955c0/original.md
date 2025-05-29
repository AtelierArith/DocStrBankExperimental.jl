```
replay(μtuner::MuTunerLogger{T}) where {T<:AbstractFloat}
```

Replay the chemical potential tuner to its current state, returning the time series for all relevant quantities. Note that this functions allocates all new arrays when it returns the time series for various quantities.
