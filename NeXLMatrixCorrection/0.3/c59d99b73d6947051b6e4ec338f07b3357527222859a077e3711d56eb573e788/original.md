```
zafcorrection(
  mctype::Type{<:MatrixCorrection},
  fctype::Type{<:FluorescenceCorrection},
  cctype::Type{<:CoatingCorrection},
  unk::Material,
  std::Material,
  cxrs,
  e0;
  unkCoating::Union{Film,AbstractVector{Film},Missing} = missing,
  stdCoating::Union{Film,AbstractVector{Film},Missing} = missing,
)
```

Constructs a tuple of MultiZAF around the mctype and fctype correction algorithms for the unknown and standard for a collection of CharXRay `cxrs`.
