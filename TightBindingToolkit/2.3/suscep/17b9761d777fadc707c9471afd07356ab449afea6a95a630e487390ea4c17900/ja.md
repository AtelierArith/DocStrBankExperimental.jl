```julia
nF_factor(Q_index::Vector{Int64}, Omega::Float64 , M::Model; eta::Float64=1e-2) --> Matrix{Matrix{ComplexF64}}
```

関数は、一般的なマルチバンドシステムにおいて、すべてのk点で $(nF(E(k)) - nF(E(k+Q))) / (Ω + i * η - (E(k+Q) - E(k)))$ を計算します。
