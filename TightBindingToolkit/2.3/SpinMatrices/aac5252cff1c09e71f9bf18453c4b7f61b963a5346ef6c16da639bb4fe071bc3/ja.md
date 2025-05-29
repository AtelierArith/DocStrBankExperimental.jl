```julia
SpinMats(spin::Rational{Int64}) --> Vector{Matrix{ComplexF64}}
```

与えられたスピン表現におけるSU(2)の3つの生成子と、d = 2*spin+1の単位行列を、[Sx, Sy, Sz, Id]の形式で返します。
