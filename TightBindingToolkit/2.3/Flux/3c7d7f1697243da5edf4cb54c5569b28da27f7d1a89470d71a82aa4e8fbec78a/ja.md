```julia
GetStringPhase(Monopoles::Vector{Vector{Float64}}, r1::Vector{Float64}, r2::Vector{Float64} ;  flux::Float64 = Float64(pi)) --> ComplexF64
```

与えられた `Monopoles` の間のディラック文字列を取得し、サイト `r1` と `r2` の間の格子上の結合を切断します。
