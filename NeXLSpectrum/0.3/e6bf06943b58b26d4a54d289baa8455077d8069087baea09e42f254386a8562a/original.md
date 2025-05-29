```
subtractcontinuum(
  spec::Spectrum,
  det::EDSDetector,
  resp::AbstractArray{<:Real,2}; #
  minE::Float64 = 1.5e3,
  maxE::Float64 = 0.95 * spec[:BeamEnergy],
  brem::Type{<:NeXLBremsstrahlung} = Castellano2004a,
  mc::Type{<:MatrixCorrection} = Riveros1993,
)::Spectrum
```

Computes the characteristic-only spectrum by subtracting the continuum.
