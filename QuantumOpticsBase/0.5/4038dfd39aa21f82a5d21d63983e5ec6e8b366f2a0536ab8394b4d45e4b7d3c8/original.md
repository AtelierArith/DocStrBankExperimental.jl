```
expiφ([T=ComplexF64,] b::ChargeBasis, k=1)
expiφ([T=ComplexF64,] b::ShiftedChargeBasis, k=1)
```

Return operator $\exp(i k φ)$ for given [`ChargeBasis`](@ref) or [`ShiftedChargeBasis`](@ref), representing the continous U(1) degree of freedom conjugate to the charge. This is a "shift" operator that shifts the charge by `k`.
