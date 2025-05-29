```
zafcorrection(
  mctype::Type{<:MatrixCorrection},
  fctype::Type{<:FluorescenceCorrection},
  cctype::Type{<:CoatingCorrection},
  mat::Material,
  cxrs,
  e0,
  coating=missing
)
```

Constructs a MultiZAF around the mctype and fctype algorithms for a collection of CharXRay `cxrs`.
