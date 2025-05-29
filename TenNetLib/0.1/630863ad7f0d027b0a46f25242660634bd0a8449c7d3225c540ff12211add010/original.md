```
function measure(::Type{ElT} = ComplexF64, psi::MPS, optens::Vector{ITensor})
```

Returns (complex / real) multi-site expectation value (`::ComplexF64` / `::Float64`) of a given MPS `psi::MPS` for a given vector of single-site operators (`optens::Vector{ITensor}`).

For `ElT = Float64`, if the expectation value is complex, raises a warning!
