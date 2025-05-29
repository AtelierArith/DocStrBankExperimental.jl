```
charXRayLabels(#
  spec::Spectrum, #
  elm::Element, #
  allElms::AbstractSet{Element}, #
  det::Detector, #
  ampl::Float64, #
  maxE::Float64=1.0e6)::Vector{SpectrumFeature}
```

Creates a vector of CharXRayLabel objects associated with 'elm' for a spectrum containing the elements 'allElms' assuming that it was collected on 'det'.  ROIs in which other elements from 'allElms' interfere with 'elm' will not be included.
