```
zafcorrection(
  mctype::Type{<:MatrixCorrection},
  fctype::Type{<:FluorescenceCorrection},
  cctype::Type{<:CoatingCorrection},
  mat::Material,
  ashell::AtomicSubShell,
  e0::Real,
  coating::Union{Film,AbstractVector{Film},Missing}
)
```

指定されたパラメータに対して蛍光モデルを使用してmctype補正モデルを使用してZAFCorrectionオブジェクトを構築します。
