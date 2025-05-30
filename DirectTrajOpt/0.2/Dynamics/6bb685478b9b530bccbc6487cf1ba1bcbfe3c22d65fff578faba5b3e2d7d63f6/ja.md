```
TrajectoryDynamics
```

軌道最適化ダイナミクスのための構造体で、単一の時間ステップダイナミクスを計算するインテグレーターと、ヤコビ行列およびヘッセ行列のための関数によって表されます。

# フィールド

  * `integrators::Union{Nothing, Vector{<:AbstractIntegrator}}`: インテグレーターのベクター。
  * `F!::Function`: 軌道ダイナミクスを計算する関数。
  * `∂F!::Function`: ダイナミクスのヤコビ行列を計算する関数。
  * `∂fs::Vector{SparseMatrixCSC{Float64, Int}}`: ヤコビ行列の行列のベクター。
  * `μ∂²F!::Union{Function, Nothing}`: ラグランジアンのヘッセ行列を計算する関数。
  * `μ∂²fs::Vector{SparseMatrixCSC{Float64, Int}}`: ヘッセ行列の行列のベクター。
  * `dim::Int`: ダイナミクスの総次元。
