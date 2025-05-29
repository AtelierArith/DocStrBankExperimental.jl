```
entropy_vn(ρ::QuantumObject; base::Int=0, tol::Real=1e-15)
```

[フォン・ノイマンエントロピー](https://en.wikipedia.org/wiki/Von_Neumann_entropy) $S = - \textrm{Tr} \left[ \hat{\rho} \log \left( \hat{\rho} \right) \right]$ を計算します。ここで、$\hat{\rho}$ は系の密度行列です。

# 注意事項

  * `ρ` は量子状態であり、[`Ket`](@ref) または [`Operator`](@ref) のいずれかです。
  * `base` は使用する対数の底を指定し、デフォルト値 `0` を使用する場合は自然対数が使用されます。
  * `tol` は密度行列 $\hat{\rho}$ のゼロ値の固有値を検出するための絶対許容誤差を示します。

# 例

純粋状態:

```jldoctest
julia> ψ = fock(2,0)

Quantum Object:   type=Ket()   dims=[2]   size=(2,)
2-element Vector{ComplexF64}:
 1.0 + 0.0im
 0.0 + 0.0im

julia> entropy_vn(ψ, base=2)
-0.0
```

混合状態:

```jldoctest
julia> ρ = maximally_mixed_dm(2)

Quantum Object:   type=Operator()   dims=[2]   size=(2, 2)   ishermitian=true
2×2 Diagonal{ComplexF64, Vector{ComplexF64}}:
 0.5-0.0im      ⋅    
     ⋅      0.5-0.0im

julia> entropy_vn(ρ, base=2)
1.0
```
