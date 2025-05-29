```
negativity(ρ::QuantumObject, subsys::Int; logarithmic::Bool=false)
```

量子状態の[ネガティビティ](https://en.wikipedia.org/wiki/Negativity_(quantum_mechanics)) $N(\hat{\rho}) = \frac{\Vert \hat{\rho}^{\Gamma}\Vert_1 - 1}{2}$ を計算します。ここで、$\hat{\rho}^{\Gamma}$ はサブシステムに関する $\hat{\rho}$ の部分転置であり、$\Vert \hat{X} \Vert_1=\textrm{Tr}\sqrt{\hat{X}^\dagger \hat{X}}$ はトレースノルムです。

# 引数

  * `ρ::QuantumObject`: 密度行列（`ρ.type` は [`Operator`](@ref) でなければなりません）。
  * `subsys::Int`: ネガティビティを計算するサブシステムを示すインデックス。
  * `logarithmic::Bool`: 対数ネガティビティを計算するかどうかを選択します。デフォルトは `false` です。

# 戻り値

  * `N::Real`: ネガティビティの値。

# 例

```jldoctest
julia> Ψ = bell_state(0, 0)

Quantum Object:   type=Ket()   dims=[2, 2]   size=(4,)
4-element Vector{ComplexF64}:
 0.7071067811865475 + 0.0im
                0.0 + 0.0im
                0.0 + 0.0im
 0.7071067811865475 + 0.0im

julia> ρ = ket2dm(Ψ)

Quantum Object:   type=Operator()   dims=[2, 2]   size=(4, 4)   ishermitian=true
4×4 Matrix{ComplexF64}:
 0.5+0.0im  0.0+0.0im  0.0+0.0im  0.5+0.0im
 0.0+0.0im  0.0+0.0im  0.0+0.0im  0.0+0.0im
 0.0+0.0im  0.0+0.0im  0.0+0.0im  0.0+0.0im
 0.5+0.0im  0.0+0.0im  0.0+0.0im  0.5+0.0im

julia> round(negativity(ρ, 2), digits=2)
0.5
```
