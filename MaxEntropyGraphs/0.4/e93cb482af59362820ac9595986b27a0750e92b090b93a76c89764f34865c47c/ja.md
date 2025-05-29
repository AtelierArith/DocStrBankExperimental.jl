```
∇L_BiCM_reduced!(∇L::AbstractVector, θ::AbstractVector, k⊥::Vector, k⊤::Vector, f⊥::Vector, f⊤::Vector,  nz⊥::UnitRange{T}, nz⊤::UnitRange{T}, x::AbstractVector, y::AbstractVector, n⊥::Int) where {T<:Signed}
```

縮小されたDBCMモデルの対数尤度の勾配を指数形式を使用して計算し、凸性を維持します。

最適化のために、この関数は特定のモデルに関連付けられた匿名関数を生成するために使用されます。この関数は、速度のために事前に割り当てられたベクトル（`∇L`、`x`、および`y`）を更新します。勾配は非割り当てです。

# 引数

  * `∇L`: 縮小モデルの対数尤度の勾配
  * `θ`: モデルの最尤推定パラメータ ([α; β])
  * `k⊥`: ⊥層の縮小次数列
  * `k⊤`: ⊤層の縮小次数列
  * `f⊥`: ⊥層の各次数の頻度
  * `f⊤`: ⊤層の各次数の頻度
  * `nz⊥`: 縮小された⊥層次数列の非ゼロ要素のインデックス
  * `nz⊤`: 縮小された⊤層次数列の非ゼロ要素のインデックス
  * `x`: モデルの指数化された最尤推定パラメータ ( xᵢ = exp(-αᵢ) )
  * `y`: モデルの指数化された最尤推定パラメータ ( yᵢ = exp(-βᵢ) )
  * `n⊥`: 縮小された⊥層次数列のユニークな値の数

# 例

```jldoctest ∇L_BiCM_reduced
# BiCMモデルでの明示的な使用:
julia> G = corporateclub();

julia> model = BiCM(G);

julia> ∇L = zeros(Real, length(model.θᵣ));

julia> x  = zeros(Real, length(model.xᵣ));

julia> y  = zeros(Real, length(model.yᵣ));

julia> ∇model_fun! = θ -> ∇L_BiCM_reduced!(∇L, θ, model.d⊥ᵣ, model.d⊤ᵣ, model.f⊥, model.f⊤, model.d⊥ᵣ_nz, model.d⊤ᵣ_nz, x, y, model.status[:d⊥_unique]);

julia> ∇model_fun!(model.θᵣ);

```
