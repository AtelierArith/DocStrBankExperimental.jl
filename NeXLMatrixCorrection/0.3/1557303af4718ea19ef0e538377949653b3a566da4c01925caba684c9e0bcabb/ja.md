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

mctypeおよびfctypeアルゴリズムの周りにMultiZAFを構築し、CharXRay `cxrs`のコレクションに対して適用します。
