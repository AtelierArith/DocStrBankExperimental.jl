```
fitcontinuum(
  spec::Spectrum,
  det::EDSDetector,
  resp::AbstractArray{<:Real,2}; #
  minE::Float64 = 1.5e3,
  maxE::Float64 = 0.95 * spec[:BeamEnergy],
  brem::Type{<:NeXLBremsstrahlung} = Castellano2004a,
  mc::Type{<:MatrixCorrection} = Riveros1993,
)
```

Fit the continuum from ROIs determined from the data within the spectrum (:Composition, :BeamEnergy & :TakeOffAngle). The ROIs are computed using `continuumrois(...)` and each roi is fit seperately.
