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

Constructs an ZAFCorrection object using the mctype correction model with the fluorescence model for the specified parameters.
