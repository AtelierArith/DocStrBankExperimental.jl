```
r2star_crsi!(
    r2s::AbstractArray{<:AbstractFloat, N-1},
    mag::AbstractArray{<:AbstractFloat, N > 1},
    TEs::AbstractVector{<:Real},
    mask::Union{Nothing, AbstractArray{Bool, N-1}} = nothing,
    M::Integer = 3,
    sigma::Union{Nothing, Real} = nothing,
    Rsz::NTuple{N-1, Integer} = size(mag)[1:N-1] .÷ 20,
) -> r2s
```

Calculation of Relaxivities by Signal Integration (CRSI) [1].

### Arguments

  * `r2s::AbstractArray{<:AbstractFloat, N-1}`: R2* map (1 / units of TEs)
  * `mag::AbstractArray{<:AbstractFloat, N > 1}`: multi-echo magnitude
  * `TEs::AbstractVector{<:Real}`: echo times
  * `mask::Union{Nothing, AbstractArray{Bool, N-1}} = nothing`:   binary mask of region of interest
  * `M::Integer = 3`: interpolation factor
  * `sigma::Union{Nothing, Real} = nothing`: noise
  * `Rsz::NTuple{N-1, Integer} = size(mag)[1:N-1] .÷ 20`:

      * `sigma isa Real`: unused
      * `sigma isa Nothing`: size of kernels used to calculate the noise from the   background signal of the magnitude.

### Returns

  * `r2s`: R2* map (1 / units of TEs)

### References

[1] Song R, Loeffler RB, Holtrop JL, McCarville MB, Hankins JS, Hillenbrand CM.     Fast quantitative parameter maps without fitting: Integration yields     accurate mono‐exponential signal decay rates.     Magnetic resonance in medicine. 2018 Jun;79(6):2978-85.
