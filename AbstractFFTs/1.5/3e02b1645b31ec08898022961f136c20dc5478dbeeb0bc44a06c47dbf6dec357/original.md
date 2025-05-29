```
rfftfreq(n, fs=1)
```

Return the discrete Fourier transform (DFT) sample frequencies for a real DFT of length `n`. The returned `Frequencies` object is an `AbstractVector` containing the frequency bin centers at every sample point. `fs` is the sampling rate of the input signal, which is the reciprocal of the sample spacing.

Given a window of length `n` and a sampling rate `fs`, the frequencies returned are

```julia
[0:n÷2;]  * fs/n  # if n is even
[0:(n-1)÷2;]  * fs/n  # if n is odd
```

!!! note
    The Nyquist-frequency component is considered to be positive, unlike [`fftfreq`](@ref).


# Examples

```jldoctest; setup=:(using AbstractFFTs)
julia> rfftfreq(4, 1)
3-element Frequencies{Float64}:
 0.0
 0.25
 0.5

julia> rfftfreq(5, 2)
3-element Frequencies{Float64}:
 0.0
 0.4
 0.8
```
