```julia
mutable struct PDESystem
```

ディリクレ境界条件を持つ単純なPDEを記述するためのすべての情報を保持する構造体。

# フィールド

  * `A::SparseArrays.SparseMatrixCSC{Float64, Int64}`: 剛性行列
  * `b::Vector{Float64}`: 荷重ベクトル
  * `bc::Vector{Float64}`: ディリクレ境界値
  * `DI::Set{Int64}`: ディリクレノード
  * `qdim::Int64`: ベクトル値状態の成分
  * `Factors::Any`: システム行列の因子分解
  * `SystemMatrix::SparseArrays.SparseMatrixCSC{Float64, Int64}`: 剛性行列とディリクレ条件のシステム
  * `B::SparseArrays.SparseMatrixCSC{Float64, Int64}`: ディリクレ射影行列
  * `state::Vector{Float64}`: 解ベクトル
  * `rhs::Vector{Float64}`: ソース項とディリクレ条件を持つ右辺ベクトル
