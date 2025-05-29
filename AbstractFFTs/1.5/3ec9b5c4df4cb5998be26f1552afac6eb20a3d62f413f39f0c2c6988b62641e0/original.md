```
fftfreq(n, fs=1)
```

Return the discrete Fourier transform (DFT) sample frequencies for a DFT of length `n`. The returned `Frequencies` object is an `AbstractVector` containing the frequency bin centers at every sample point. `fs` is the sampling rate of the input signal, which is the reciprocal of the sample spacing.

Given a window of length `n` and a sampling rate `fs`, the frequencies returned are

```julia
[0:n÷2-1; -n÷2:-1]  * fs/n   # if n is even
[0:(n-1)÷2; -(n-1)÷2:-1]  * fs/n  # if n is odd
```

# Examples

```jldoctest; setup=:(using AbstractFFTs)
julia> fftfreq(4, 1)
4-element Frequencies{Float64}:
  0.0
  0.25
 -0.5
 -0.25

julia> fftfreq(5, 2)
5-element Frequencies{Float64}:
  0.0
  0.4
  0.8
 -0.8
 -0.4
```
