```
psi_lower(N::Integer, B::NfFactorBase) -> Vector{Int}, ZZAbsPowerSeriesRingElem
psi_lower(N::ZZRingElem, B::NfFactorBase) -> Vector{Int}, ZZAbsPowerSeriesRingElem

psi_upper(N::Integer, B::NfFactorBase) -> Vector{Int}, ZZAbsPowerSeriesRingElem
psi_upper(N::ZZRingElem, B::NfFactorBase) -> Vector{Int}, ZZAbsPowerSeriesRingElem
```

Uses Bernstein's techniques to bound the number of ideals $A$ of norm bounded by $N$ that are smooth over the factor base $B$.
