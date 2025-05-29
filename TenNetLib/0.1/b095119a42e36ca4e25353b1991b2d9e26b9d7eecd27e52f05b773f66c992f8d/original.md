```
function measure(::Type{ElT} = ComplexF64, psi::TTN, opstr::String, pos::Int)
```

Returns (complex / real) local expectation value (`::ComplexF64` / `::Float64`) of a given TTN `psi::TTN` for a given operator name (`opstr::String`) and a site index (`pos::Int`) 

For `ElT = Float64`, if the expectation value is complex, raises a warning!
