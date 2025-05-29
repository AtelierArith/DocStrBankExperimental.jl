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

Creates a matched pair of ZAFCorrection objects using the matrix correction algorithm for the specified unknown and standard.
