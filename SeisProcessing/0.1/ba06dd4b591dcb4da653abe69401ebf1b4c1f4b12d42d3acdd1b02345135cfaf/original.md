```
SeisKolmogoroff(in)
```

Transform a wavelet into its minimum phase equivalent.

# Arguments

  * `in::Array{Real,1}`: input wavelet.

# Example

```julia
julia> using PyPlot
julia> w = Ricker()
julia> wmin = SeisKolmogoroff(w)
julia> plot(w); plot(wmin)
```

# Reference

  * Claerbout, Jon F., 1976, Fundamentals of geophysical data processing.

McGraw-Hill Inc.
