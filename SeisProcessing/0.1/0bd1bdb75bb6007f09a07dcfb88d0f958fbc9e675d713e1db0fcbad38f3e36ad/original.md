```
Ricker(; <keyword arguments>)
```

Create a Ricker wavelet.

# Arguments

  * `dt=0.002`: sampling interval in secs.
  * `f0=20.0`: central frequency in Hz.

# Examples

```julia
julia> w = Ricker(); plot(w);
julia> w = Ricker(dt=0.004, f0=20); plot(w);
```

# Reference

Sheriff, Robert, 2002, Encyclopedic Dictionary of Applied Geophysics, fourth ed.: Society of Exploration Geophysicists. Geophysical Reference Series No. 13.
