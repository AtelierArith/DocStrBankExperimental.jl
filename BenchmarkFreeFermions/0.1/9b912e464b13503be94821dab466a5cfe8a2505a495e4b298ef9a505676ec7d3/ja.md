```
 TimeCorrelation(ξ::Vector{Float64},
      V::Matrix,
      β::Real,
      si::Vector{Int64},
      dagidx::Vector{Int64},
      lsτ::AbstractVector{<:Number}) -> ::Float64(::ComplexF64)
```

シフトされた単一粒子スペクトル `ξ = ϵ - μ` と、`Tij = - V diagm(ϵ) V'` から得られた固有ベクトル `V` を用いて時間相関関数を返します。`si` はサイトを示し、`dagidx` は演算子がダガーかどうかを示します。`lsτ` は `si` と同じ長さを持ち、各演算子の時間を示します。例えば、`si = [i, j, k, l]`、`dagidx = [1, 3]` および `lsτ = [τ1, τ2, 0, 0]` は `c_i^dag(τ1) c_j(τ2) c_k^dag c_l` を意味します。   
