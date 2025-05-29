```
DBCM_reduced_iter!(θ::AbstractVector, k_out::AbstractVector, k_in::AbstractVector, F::AbstractVector, nz_out::Vector, nz_in::Vector,x::AbstractVector, y::AbstractVector, G::AbstractVector, H::AbstractVector, n::Int)
```

DBCMモデルの次の固定点反復を指数形式を使用して計算し、凸性を維持します。この関数は非割り当てであり、速度のために事前に割り当てられたベクトル（`θ`、`x`、`y`、および`G`）を更新します。

# 引数

  * `θ`: モデルの最尤パラメータ（[α; β]）
  * `k_out`: 簡略化された出次数列
  * `k_in`: 簡略化された入次数列
  * `F`: 次数列内の各ペアの頻度
  * `nz_out`: 簡略化された出次数列の非ゼロ要素のインデックス
  * `nz_in`: 簡略化された入次数列の非ゼロ要素のインデックス
  * `x`: モデルの指数化された最尤パラメータ（xᵢ = exp(-αᵢ)）
  * `y`: モデルの指数化された最尤パラメータ（yᵢ = exp(-βᵢ)）
  * `G`: 計算用のバッファ
  * `n`: 簡略化されたモデルのノード数

# 例

```jldoctest
# DBCMモデルで使用：
julia> G = MaxEntropyGraphs.Graphs.SimpleDiGraph(rhesus_macaques());

julia> model = DBCM(G);

julia> G = zeros(eltype(model.θᵣ), length(model.θᵣ));

julia> H = zeros(eltype(model.θᵣ), length(model.yᵣ));

julia> x = zeros(eltype(model.θᵣ), length(model.xᵣ));

julia> y = zeros(eltype(model.θᵣ), length(model.yᵣ));

julia> DBCM_FP! = θ -> DBCM_reduced_iter!(θ, model.dᵣ_out, model.dᵣ_in, model.f, model.dᵣ_out_nz, model.dᵣ_in_nz, x, y, G, model.status[:d_unique]);

julia> DBCM_FP!(model.θᵣ);

```
