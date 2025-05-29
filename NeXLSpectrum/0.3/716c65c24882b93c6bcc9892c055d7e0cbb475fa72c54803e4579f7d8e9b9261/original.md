```
fitcontinuum(
  spec::Spectrum,
  resp::AbstractArray,
  rois::Vector{UnitRange};
  brem::Type{<:NeXLBremsstrahlung} = Castellano2004a,
  mc::Type{<:MatricCorrection} = Riveros1993,
)

Fit a continuum model to the specified range of channels (`rois`).  The `resp` argument is a matrix which describes
```

the detector response on a channel-by-channel basis.  It can be calculated from an `EDSDetector` and an `DetectorEfficiency` using `resp = NeXLSpectrum.detectorresponse(det, eff)`.  The `Spectrum` object must have the :Composition, :BeamEnergy and :TakeOffAngle properties defined.
