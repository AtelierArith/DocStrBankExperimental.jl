```
energy_map(Xw, y, method)
```

Computes the energy map based on the decomposed input signals `Xw` and corresponding labels `y`.

# Arguments

  * `Xw::AbstractArray{S} where S<:AbstractFloat`: Decomposed 1D or 2D signals.
  * `y::AbstractVector{T} where T`: Corresponding labels to the signals in `Xw`.
  * `method::EnergyMap`: Type of energy map to compute. Supported types are:

      * `TimeFrequency()`
      * `ProbabilityDensity()`
      * `Signatures()`

# Returns

  * `Γ`: Computed energy map. Depending on the input `method`, the data structure of `Γ` is:

      * `TimeFrequency()` $\Longrightarrow$ `Array{S,3}` for 1D signals or `Array{S,4}` for 2D signals.
      * `ProbabilityDensity()` $\Longrightarrow$ `Array{S,4}` for 1D signals or `Array{S,5}` for 2D signals.
      * `Signatures(weight = :equal)`: $\Longrightarrow$ Vector{NamedTuple{(:coef, :weight), Tuple{Array{S}, S}}}
      * `Signatures(weight = :pdf`: $\Longrightarrow$ Vector{NamedTuple{(:coef, :weight), Tuple{Array{S}, Array{S}}}}

!!! tip
    When setting `method = Signatures()` of any type of weight, the output is a vector of named tuples, where each named tuple contains the coefficients and weights of all the signals of the same label.


# Examples

```julia
using Wavelets, WaveletsExt

X, y = generateclassdata(ClassData(:tri, 5, 5, 5))
Xw = wpdall(X, wavelet(WT.haar))

energy_map(Xw, y, TimeFrequency())
energy_map(Xw, y, ProbabilityDensity())
energy_map(Xw, y, Signatures())
```

**See also:** [`EnergyMap`](@ref). [`TimeFrequency`](@ref), [`ProbabilityDensity`](@ref)
