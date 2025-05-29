```
psi_lower(N::Integer, B::NfFactorBase) -> Vector{Int}, ZZAbsPowerSeriesRingElem
psi_lower(N::ZZRingElem, B::NfFactorBase) -> Vector{Int}, ZZAbsPowerSeriesRingElem

psi_upper(N::Integer, B::NfFactorBase) -> Vector{Int}, ZZAbsPowerSeriesRingElem
psi_upper(N::ZZRingElem, B::NfFactorBase) -> Vector{Int}, ZZAbsPowerSeriesRingElem
```

バーンスタインの手法を使用して、因子基 $B$ に対して滑らかなノルムが $N$ 以下の理想 $A$ の数を制限します。
