```
BiCM_reduced_iter!(θ::AbstractVector, k⊥::Vector, k⊤::Vector, f⊥::Vector, f⊤::Vector, nz⊥::UnitRange{T}, nz⊤::UnitRange{T}, x::AbstractVector, y::AbstractVector, G::AbstractVector, n⊥::Int) where {T<:Signed}
```

BiCMモデルの次の不動点反復を指数形式を使用して計算し、凸性を維持します。この関数はメモリを割り当てず、事前に割り当てられたベクトル（`θ`、`x`、`y`、および`G`）を更新して速度を向上させます。

# 引数

  * `θ`: モデルの最尤パラメータ ([α; β])
  * `k⊥`: ⊥層の縮小次数列
  * `k⊤`: ⊤層の縮小次数列
  * `f⊥`: ⊥層の各次数の頻度
  * `f⊤`: ⊤層の各次数の頻度
  * `nz⊥`: 縮小された⊥層次数列の非ゼロ要素のインデックス
  * `nz⊤`: 縮小された⊤層次数列の非ゼロ要素のインデックス
  * `x`: モデルの指数化された最尤パラメータ ( xᵢ = exp(-αᵢ) )
  * `y`: モデルの指数化された最尤パラメータ ( yᵢ = exp(-βᵢ) )
  * `G`: 計算用のバッファ
  * `n⊥`: 縮小された⊥層次数列のユニークな値の数

# 例

```jldoctest
# BiCMモデルで使用:
julia> G = corporateclub();

julia> model = BiCM(G);

julia> G = zeros(eltype(model.θᵣ), length(model.θᵣ));

julia> x = zeros(eltype(model.θᵣ), length(model.xᵣ));

julia> y = zeros(eltype(model.θᵣ), length(model.yᵣ));


julia> BiCM_FP! = θ -> BiCM_reduced_iter!(θ, model.d⊥ᵣ, model.d⊤ᵣ, model.f⊥, model.f⊤, model.d⊥ᵣ_nz, model.d⊤ᵣ_nz, x, y, G, model.status[:d⊥_unique]);

julia> BiCM_FP!(model.θᵣ);

```
