```
∇L_DBCM_reduced!(∇L::AbstractVector, θ::AbstractVector, k_out::AbstractVector, k_in::AbstractVector, F::AbstractVector, nz_out::Vector, nz_in::Vector, x::AbstractVector, y::AbstractVector,n::Int)
```

縮小されたDBCMモデルの対数尤度の勾配を指数形式を用いて計算し、凸性を維持します。

最適化のために、この関数は特定のモデルに関連付けられた匿名関数を生成するために使用されます。この関数は、速度のために事前に割り当てられたベクトル（`∇L`、`x`、および`y`）を更新します。勾配は非割り当てです。

# 引数

  * `∇L`: 縮小モデルの対数尤度の勾配
  * `θ`: モデルの最尤推定パラメータ ([α; β])
  * `k_out`: 縮小された出次数列
  * `k_in`: 縮小された入次数列
  * `F`: 次数列における各ペアの頻度
  * `nz_out`: 縮小された出次数列における非ゼロ要素のインデックス
  * `nz_in`: 縮小された入次数列における非ゼロ要素のインデックス
  * `x`: モデルの指数化された最尤推定パラメータ ( xᵢ = exp(-αᵢ) )
  * `y`: モデルの指数化された最尤推定パラメータ ( yᵢ = exp(-βᵢ) )
  * `n`: 縮小モデルのノード数

# 例

```jldoctest ∇L_DBCM_reduced
# DBCMモデルでの明示的な使用:
julia> G = MaxEntropyGraphs.Graphs.SimpleDiGraph(rhesus_macaques());

julia> model = DBCM(G);

julia> ∇L = zeros(Real, length(model.θᵣ));

julia> x  = zeros(Real, length(model.xᵣ));

julia> y  = zeros(Real, length(model.yᵣ));

julia> ∇model_fun! = θ -> ∇L_DBCM_reduced!(∇L, θ, model.dᵣ_out, model.dᵣ_in, model.f, model.dᵣ_out_nz, model.dᵣ_in_nz, x, y, model.status[:d_unique]);

julia> ∇model_fun!(model.θᵣ);

```

```jldoctest ∇L_DBCM_reduced
# optimisation.jlフレームワーク内での使用:
julia> fun = (θ,p) -> -L_DBCM_reduced(θ, model.dᵣ_out, model.dᵣ_in, model.f, model.dᵣ_out_nz, model.dᵣ_in_nz, model.status[:d_unique]);

julia> x  = zeros(Real, length(model.xᵣ)); # バッファを初期化

julia> y  = zeros(Real, length(model.yᵣ));#  バッファを初期化

julia> ∇fun! = (∇L, θ, p) -> ∇L_DBCM_reduced!(∇L, θ, model.dᵣ_out, model.dᵣ_in, model.f, model.dᵣ_out_nz, model.dᵣ_in_nz, x, y, model.status[:d_unique]);

julia> θ₀ = initial_guess(model); # 初期条件

julia> foo = MaxEntropyGraphs.Optimization.OptimizationFunction(fun, grad=∇fun!); # 目的関数を定義

julia> prob  = MaxEntropyGraphs.Optimization.OptimizationProblem(foo, θ₀); # 最適化問題を定義

julia> method = MaxEntropyGraphs.OptimizationOptimJL.LBFGS(); # 最適化手法を設定

julia> MaxEntropyGraphs.Optimization.solve(prob, method); # 解決する
```
