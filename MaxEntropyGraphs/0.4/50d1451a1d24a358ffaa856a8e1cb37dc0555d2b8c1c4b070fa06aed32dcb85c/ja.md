```
∇L_UBCM_reduced!(∇L::Vector, θ::Vector, K::Vector, F::Vector, x::Vector)
```

縮小されたUBCMモデルの対数尤度の勾配を指数形式を用いて計算します（凸性を維持するため）。

最適化のために、この関数は特定のモデルに関連付けられた匿名関数を生成するために使用されます。勾配は非割り当てであり、速度のために事前に割り当てられたベクトル（`∇L`と`x`）を更新します。

# 引数

  * `∇L`: 縮小モデルの対数尤度の勾配
  * `θ`: モデルの最尤パラメータ
  * `K`: 縮小された次数列
  * `F`: 次数列における各次数の頻度
  * `x`: モデルの指数化された最尤パラメータ（ xᵢ = exp(-θᵢ) ）

# 例

```jldoctest
# UBCMモデルでの明示的な使用:
julia> G = MaxEntropyGraphs.Graphs.SimpleGraphs.smallgraph(:karate);

julia> model = UBCM(G);

julia> ∇L = zeros(Real, length(model.θᵣ));

julia> x  = zeros(Real, length(model.θᵣ));

julia> ∇model_fun! = θ -> ∇L_UBCM_reduced!(∇L, θ, model.dᵣ, model.f, x);

julia> ∇model_fun!(model.θᵣ);

```

```jldoctest
# optimisation.jlフレームワーク内での使用:
julia> model = UBCM(MaxEntropyGraphs.Graphs.SimpleGraphs.smallgraph(:karate));

julia> fun =  (θ, p) ->  - L_UBCM_reduced(θ, model.dᵣ, model.f);

julia> x  = zeros(Real, length(model.θᵣ)); # 勾配バッファを初期化

julia> ∇fun! = (∇L, θ, p) -> ∇L_UBCM_reduced!(∇L, θ, model.dᵣ, model.f, x); # 勾配を定義

julia> θ₀ = initial_guess(model); # 初期条件

julia> foo = MaxEntropyGraphs.Optimization.OptimizationFunction(fun, grad=∇fun!); # 目的関数を定義 

julia> prob  = MaxEntropyGraphs.Optimization.OptimizationProblem(foo, θ₀); # 最適化問題を定義

julia> method = MaxEntropyGraphs.OptimizationOptimJL.LBFGS(); # 最適化手法を設定

julia> MaxEntropyGraphs.Optimization.solve(prob, method); # 解決する

```
