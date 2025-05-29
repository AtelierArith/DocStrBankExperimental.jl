```julia
SpectralFunction(H::Array{Matrix{ComplexF64}, N}, omega::Float64 ;  spread::Float64 = 1e-3):: Array{Matrix{ComplexF64}} where {N}
```

ハミルトニアン、周波数、およびスプレッドを考慮して行列スペクトル関数を返します。
