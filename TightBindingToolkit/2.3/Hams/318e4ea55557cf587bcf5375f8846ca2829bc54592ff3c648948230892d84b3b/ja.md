```julia
FillHoppingHamiltonian(uc::UnitCell, k::Vector{Float64} ; OnSiteMatrices::Vector{Matrix{ComplexF64}}) --> Matrix{ComplexF64}
```

運動量点 `k` におけるホッピングハミルトニアンを返します。これは `UnitCell` に存在する結合に対応しています。`OnSiteMatrices` は場に使用され、最後の行列が化学ポテンシャルに対応するものとします。
