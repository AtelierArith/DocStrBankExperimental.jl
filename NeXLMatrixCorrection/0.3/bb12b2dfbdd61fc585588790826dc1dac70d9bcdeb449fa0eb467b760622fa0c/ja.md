```
zafcorrection(
   mctype::Type{<:MatrixCorrection},
   fctype::Type{<:FluorescenceCorrection},
   cctype::Type{<:CoatingCorrection},
   unk::Material,
   std::Material,
   ashell::AtomicSubShell,
   e0::Real;
   unkCoating::Union{Film,AbstractVector{Film},Missing} = missing,
   stdCoating::Union{Film,AbstractVector{Film},Missing} = missing,
)
```

指定された未知および標準に対して、マトリックス補正アルゴリズムを使用してZAFCorrectionオブジェクトの一致したペアを作成します。
