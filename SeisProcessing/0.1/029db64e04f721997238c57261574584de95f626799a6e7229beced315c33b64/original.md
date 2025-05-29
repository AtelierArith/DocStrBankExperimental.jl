```
Berlage(; <keyword arguments>)
```

Create a Berlage wavelet.

# Arguments

  * `dt=0.002`: sampling interval in secs.
  * `f0=20.0`: central frequency in Hz.
  * `m::Real=2`: exponential parameter of Berlage wavelet.
  * `alpha::Real=180.0`: alpha parameter of Berlage wavelet in rad/secs.
  * `phi0::Real`: phase rotation in radians.

# Example

```julia
julia> w = Berlage(); plot(w);
```

**Reference**

  * Aldridge, David F., 1990, The berlage wavelet: GEOPHYSICS, 55, 1508–1511.
