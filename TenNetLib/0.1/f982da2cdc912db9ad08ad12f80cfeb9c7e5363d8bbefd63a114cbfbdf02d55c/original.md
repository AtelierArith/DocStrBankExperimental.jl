```
function measure(::Type{ElT} = ComplexF64, psi::MPS, oppairs::Vector{Pair{String, Int}};
                 isfermions::Bool = true)
```

Returns (complex / real) multi-site expectation value (`::ComplexF64` / `::Float64`) of a given MPS `psi::MPS`. `oppairs::Vector{Pair{String, Int}}` contains pairs of operator names (`String`) and site locations (`Int`). E.g., for <ψ|OᵢOⱼOₖ... |ψ>, `oppairs = ["O" => i, "O" => j, "O" => k,...]`.

Fermionic JW strings are added automatically for fermionic operators if `isfermions::Bool = true` (default).

For `ElT = Float64`, if the expectation value is complex, raises a warning!

#### Example:

```
valueC = measure(psi, ["Cdag" => 2, "C" => 6, "Cdag" => 9, "C" => 12])
valueR = measure(Float64, psi, ["Cdag" => 2, "C" => 6, "Cdag" => 9, "C" => 12])
```
