```
chargeop([T=ComplexF64,] b::ChargeBasis)
chargeop([T=ComplexF64,] b::ShiftedChargeBasis)
```

与えられた [`ChargeBasis`](@ref) または [`ShiftedChargeBasis`](@ref) に対する対角電荷演算子 $N$ を返します。
