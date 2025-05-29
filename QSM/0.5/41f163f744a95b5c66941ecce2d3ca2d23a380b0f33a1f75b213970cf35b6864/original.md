```
makewindow(
    sz::NTuple{2, Integer},
    wsz::Union{Integer, NTuple{2, Integer}},
    window::Symbol,
    args...
) -> Array{Float64, 2}
```

2d k-space window.

The window is centered at index `(1,1)`. This function is a wrapper for DSP.jl's `makewindow(window, n = wsz, padding = sz - wsz, zerophase=true)`.

### Arguments

  * `sz::NTuple{2, Integer}`: array size
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

  * `Array{Float64, 2}:` window
