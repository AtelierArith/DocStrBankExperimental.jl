```
homodyne(
    u::AbstractArray{<:Complex{<:AbstractFloat}, N > 1},
    wsz::Union{Integer, NTuple{2, Integer}},
    window::Symbol,
    args...
) -> typeof(similar(u))

homodyne!(
    u::AbstractArray{<:Complex{<:AbstractFloat}, N > 1},
    wsz::Union{Integer, NTuple{2, Integer}},
    window::Symbol,
    args...
) -> u

homodyne!(
    v::AbstractArray{<:Complex{<:AbstractFloat}, N > 1},
    u::AbstractArray{<:Complex{<:AbstractFloat}, N},
    wsz::Union{Integer, NTuple{2, Integer}},
    window::Symbol,
    args...
) -> v
```

Homodyne filter.

Filter by applying 2d window to k-space of complex data: `u / F^-1(w * F(u))`.

### Arguments

  * `u::AbstractArray{<:Complex{<:AbstractFloat}, N > 1}`:   complex (multi-echo) data
  * `wsz::Union{Integer, NTuple{2, Integer}}`: window size
  * `window::Symbol`: window function

      * `:fermi`: `w = 1 / (1 + exp((x-radius) / width)), x ∈ [-0.5, 0.5]`
      * `:gaussian`: `w = exp(-0.5*(x/σ)^2), x ∈ [-0.5, 0.5]`
      * `:hamming`: `w = 0.54 + 0.46*cos(2π*x), x ∈ [-0.5, 0.5]`
      * `:hann`: `w = 0.5*(1 + cos(2π*x)), x ∈ [-0.5, 0.5]`
  * `args...`:

      * `window == :fermi`: `radius::Real, width::Real`
      * `window == :gaussian`: `σ::Real`
      * otherwise: unused

### Returns

  * `typeof(similar(u)) / u / v`: homodyne filtered complex (multi-echo) data
