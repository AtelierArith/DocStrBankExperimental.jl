```
AlgoData(; kwargs...) 
AlgoData(T::DataType; kwargs...)
```

[`fps_solve`](@ref) 呼び出しで使用されるすべてのパラメータを含む構造体。`T` はアルゴリズムで使用されるデータ型で、デフォルトは `Float64` です。`AlgoData` 構造体を返します。

# 引数

キーワード引数には以下が含まれる場合があります：

  * `σ_0::Real = T(1e3)`: サブプロブレムのパラメータ σ を初期化します；
  * `σ_max::Real = 1 / √eps(T)`: サブプロブレムのパラメータ σ の最大値；
  * `σ_update::Real = T(2)`: サブプロブレムのパラメータ σ を更新します；
  * `ρ_0::Real = one(T)`: サブプロブレムのパラメータ ρ を初期化します；
  * `ρ_max::Real = 1 / √eps(T)`: サブプロブレムのパラメータ ρ の最大値；
  * `ρ_update::Real = T(2)`: サブプロブレムのパラメータ ρ を更新します；
  * `δ_0::Real = √eps(T)`: サブプロブレムのパラメータ δ を初期化します；
  * `δ_max::Real = 1 / √eps(T)`: サブプロブレムのパラメータ δ の最大値；
  * `δ_update::Real = T(10)`: サブプロブレムのパラメータ δ を更新します；
  * `η_1::Real = zero(T)`: サブプロブレムのパラメータ η を初期化します；
  * `η_update::Real = one(T)`: サブプロブレムのパラメータ η を更新します；
  * `yM::Real = typemax(T)`: ラグランジュ乗数の上限；
  * `Δ::Real = T(0.95)`: 2つの反復間の実現可能性の期待される減少；
  * `subproblem_solver::Function = ipopt`: サブプロブレムに使用されるソルバー；
  * `subpb_unbounded_threshold::Real = 1 / √eps(T)`: この値の逆数未満では、サブプロブレムは無限大です；
  * `subsolver_max_iter::Int = 20000`: サブプロブレムソルバーの最大反復回数；
  * `atol_sub::Function = atol -> atol`: `atol` の関数におけるサブプロブレムの絶対許容誤差；
  * `rtol_sub::Function = rtol -> rtol`: `rtol` の関数におけるサブプロブレムの相対許容誤差；
  * `hessian_approx = Val(2)`: `Val(1)` または `Val(2)` のいずれかで、ヘッセ行列の近似を選択します；
  * `convex_subproblem::Bool = false`: サブプロブレムが凸である場合は true。`knitro` で `convex` オプションを設定するのに便利です；
  * `lagrange_bound::T = 1 / sqrt(eps(T))`: ラグランジュ乗数の上限。

詳細については、パッケージのドキュメント [fine-tuneFPS.md](https://JuliaSmoothOptimizers.github.io/FletcherPenaltySolver.jl/dev/fine-tuneFPS/) を参照してください。
