モデルパラメータ推定に使用されるライブラリ/アルゴリズムを指定します。このタイプを継承してカスタムモデルフィッティングアルゴリズムを定義します。

例: `struct CustomFitter <: ModelFitter{MAP} ... end` または `struct CustomFitter <: ModelFitter{BI} ... end`

すべてのモデルフィッターは *次のことを実装する必要があります*: `estimate_parameters(model_fitter::CustomFitter, problem::BossProblem; info::Bool)`。

このメソッドはタプル `(params, val)` を返す必要があります。返される `params` は `ModelParams` であるべきです（`CustomAlg <: ModelFitter{MAP}` の場合）または `AbstractVector{<:ModelParams}` であるべきです（`CustomAlg <: ModelFitter{BI}` の場合）。返される `val` はパラメータの対数尤度であるべきです（`CustomAlg <: ModelFitter{MAP}` の場合）、または個々のパラメータサンプルの対数尤度のベクトルであるべきです（`CustomAlg <: ModelFitter{BI}` の場合）、または `nothing` です。

参照: [`OptimizationMAP`](@ref), [`TuringBI`](@ref)
