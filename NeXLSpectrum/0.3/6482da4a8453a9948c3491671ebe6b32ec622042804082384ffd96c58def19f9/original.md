```
dose(spec::Spectrum, def=missing)
dose(props::Dict{Symbol, Any}, def=missing)
```

The probe dose in nA⋅s and is equals spec[:LiveTime]⋅spec[:ProbeCurrent].
