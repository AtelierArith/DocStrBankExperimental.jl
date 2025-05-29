```
 SingleParticleSpectrum(Tij::AbstractMatrix) -> ϵ::Vector{Float64}
```

ホッピング行列 `Tij` を数値的に対角化して単一粒子スペクトル `ϵ` を得ます。規約は `H = - \sum_ij Tij c_i^dag c_j` です。
