```
discriminant_measure(Γ, dm)
```

Computes the discriminant measure of each subspace calculated from the energy maps.

# Arguments

  * `Γ`: Energy map computed from `energy_map` function. The data structures of `Γ`, depending on their corresponding energy map, should be:

      * `TimeFrequency()`: `AbstractArray{T,3}` for 1D signals or `AbstractArray{T,4}` for 2D signals.
      * `ProbabilityDensity()`: `AbstractArray{T,4}` for 1D signals or `AbstractArray{T,5}` for 2D signals.
      * `Signatures()`: `AbstractVector{NamedTuple{(:coef, :weight), Tuple{S₁,S₂}}}`.
  * `dm::DiscriminantMeasure`: Type of Discriminant Measure. The type of `dm` must match the type of `Γ`.

# Returns

  * `D::Array{T}`: Discriminant measure at each coefficient of the decomposed signals.

# Examples

```julia
using Wavelets, WaveletsExt

X, y = generateclassdata(ClassData(:tri, 5, 5, 5))
Xw = wpdall(X, wavelet(WT.haar))

Γ = energy_map(Xw, y, TimeFrequency()); discriminant_measure(Γ, AsymmetricRelativeEntropy())
Γ = energy_map(Xw, y, ProbabilityDensity()); discriminant_measure(Γ, LpDistance())
Γ = energy_map(Xw, y, Signatures()); discriminant_measure(Γ, EarthMoverDistance())
```

**See also:** [`pairwise_discriminant_measure`](@ref)
