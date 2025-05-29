```
function measure(::Type{ElT} = ComplexF64, psi::TTN, opten::ITensor)
```

Returns (complex / real) local expectation value (`::ComplexF64` / `::Float64`) of a given TTN `psi::TTN`. The operator `opten::ITensor` must be single-site operator.

For `ElT = Float64`, if the expectation value is complex, raises a warning!
