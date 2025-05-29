```julia
DOS(Omega::Float64, Ham::Hamiltonian; till_band::Int64=length(Ham.bands[1, 1]), spread::Float64=1e-3) --> Float64
DOS(Omegas::Vector{Float64}, Ham::Hamiltonian; till_band::Int64=length(Ham.bands[1, 1]), spread::Float64=1e-3) --> Vector{Float64}
```

与えられたエネルギー `Omegas` に対応する状態密度を計算します。最も低いバンドを `till_band` まで計算します。計算はデルタ関数の和の有限の `spread` で行われます。
