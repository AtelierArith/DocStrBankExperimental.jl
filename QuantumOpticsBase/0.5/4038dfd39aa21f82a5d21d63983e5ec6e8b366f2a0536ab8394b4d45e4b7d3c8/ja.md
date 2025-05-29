```
expiφ([T=ComplexF64,] b::ChargeBasis, k=1)
expiφ([T=ComplexF64,] b::ShiftedChargeBasis, k=1)
```

与えられた [`ChargeBasis`](@ref) または [`ShiftedChargeBasis`](@ref) に対して演算子 $\exp(i k φ)$ を返します。これは、電荷に対して共役な連続 U(1) 自由度を表します。これは、電荷を `k` だけシフトする「シフト」演算子です。
