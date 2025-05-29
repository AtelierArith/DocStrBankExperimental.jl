```julia
mutable struct SystemState{Tv, Tp, TMatrix<:AbstractArray{Tv, 2}, TGenericMatrix, TSolArray<:AbstractArray{Tv, 2}, TData}
```

有限体積システムの状態情報を保持する構造体。

型パラメータ:

  * Tv: 解ベクトルと行列の要素型
  * TMatrix: 行列型
  * TSolArray: 解ベクトルの型: (Matrix または SparseMatrixCSC)
  * TData: ユーザーデータの型

型フィールド:

  * `system::VoronoiFVM.System`: 関連する有限体積システム
  * `data::Any`: ユーザーデータ
  * `solution::AbstractMatrix`: 解ベクトル
  * `matrix::AbstractMatrix`: 非線形問題のヤコビ行列
  * `generic_matrix::Any`: 一般的な演算子処理のためのスパース行列
  * `dudp::Vector{TSolArray} where {Tv, TSolArray<:AbstractMatrix{Tv}}`: パラメータ導関数（解配列のベクトル）
  * `update::AbstractMatrix`: ニュートン更新を保持するベクトル
  * `residual::AbstractMatrix`: ニュートン残差を保持するベクトル
  * `linear_cache::Union{Nothing, LinearSolve.LinearCache}`: 線形ソルバキャッシュ
  * `params::Vector`: パラメータベクトル
  * `uhash::UInt64`: アセンブリが呼び出された最新の未知数ベクトルのハッシュ値（微分方程式インターフェースで使用）
  * `history::Union{Nothing, VoronoiFVM.DiffEqHistory}`: 解プロセスの履歴記録（微分方程式インターフェースで使用）
