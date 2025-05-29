```
mother(this::CWT{W, T, <:ContWaveClass, N}, s::Real, nInOctave::Int,
    ω::AbstractArray{<:Real,1}) where {W, T, N} -> daughter
```

Given a CWT object, return a rescaled version of the mother wavelet, in the fourier domain. ω is the frequency, which is fftshift-ed. s is the scale variable.
