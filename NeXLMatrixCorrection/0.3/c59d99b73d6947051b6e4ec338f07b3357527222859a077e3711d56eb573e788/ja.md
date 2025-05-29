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

未知および標準のための mctype および fctype 補正アルゴリズムに基づく MultiZAF のタプルを、CharXRay `cxrs` のコレクションに対して構築します。
