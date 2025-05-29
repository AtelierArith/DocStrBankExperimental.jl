```julia
nF_factor(Q_index::Vector{Int64}, Omega::Float64 , M::Model; eta::Float64=1e-2) --> Matrix{Matrix{ComplexF64}}
```

function to calculate $(nF(E(k)) - nF(E(k+Q))) / (Ω + i * η - (E(k+Q) - E(k)))$ for a general multi-band system, at all k-points.
