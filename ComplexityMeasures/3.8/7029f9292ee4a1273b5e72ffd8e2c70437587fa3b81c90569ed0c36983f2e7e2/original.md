```
RectangularBinning(ϵ, precise = false) <: AbstractBinning
```

Rectangular box partition of state space using the scheme `ϵ`, deducing the histogram extent and bin width from the input data.

`RectangularBinning` is a convenience struct. It is re-cast into [`FixedRectangularBinning`](@ref) once the data are provided, so see that docstring for info on the bin calculation and the meaning of `precise`.

Binning instructions are deduced from the type of `ϵ` as follows:

1. `ϵ::Int` divides each coordinate axis into `ϵ` equal-length intervals  that cover all data.
2. `ϵ::Float64` divides each coordinate axis into intervals of fixed size `ϵ`, starting  from the axis minima until the data is completely covered by boxes.
3. `ϵ::Vector{Int}` divides the i-th coordinate axis into `ϵ[i]` equal-length  intervals that cover all data.
4. `ϵ::Vector{Float64}` divides the i-th coordinate axis into intervals of fixed size  `ϵ[i]`, starting from the axis minima until the data is completely covered by boxes.

`RectangularBinning` ensures all input data are covered by extending the created ranges if need be.
