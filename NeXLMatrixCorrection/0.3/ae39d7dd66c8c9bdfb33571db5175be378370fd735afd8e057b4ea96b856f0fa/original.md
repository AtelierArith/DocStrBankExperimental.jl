```
estimatecoating(substrate::Material, coating::Material, kcoating::KRatio, mc::Type{<:MatrixCorrection}=XPP)::Film
```

Use the measured k-ratio to estimate the mass-thickness of the coating material on the specified substrate. Return the result as a Film which may be assigned to the :Coating property for k-ratios associated with the substrate.

Assumptions:

  * The coating is the same for all measurements of the unknown
  * The coating element k-ratio is assumed to be assigned to the brightest line
