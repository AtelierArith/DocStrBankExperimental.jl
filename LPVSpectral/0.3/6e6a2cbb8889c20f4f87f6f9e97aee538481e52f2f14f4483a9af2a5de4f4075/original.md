```
M = mel(fs::Real, nfft::Int; nmels::Int = 128, fmin::Real = 0f0, fmax::Real = fs/2f0)
```

Returns a Mel matrix `M` such that `M*f` is a mel spectrogram if `f` is a vector of spectrogram powers, e.g.,

```julia
M*abs2.(rfft(sound))
```
