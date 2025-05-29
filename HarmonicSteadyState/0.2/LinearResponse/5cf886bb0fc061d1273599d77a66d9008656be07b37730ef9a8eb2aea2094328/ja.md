```julia
get_jacobian_response(
    res::HarmonicSteadyState.Result{D, S, P, F} where F<:FunctionWrappers.FunctionWrapper{Array{S, 2}, Tuple{Array{S, 1}}},
    nat_var::Symbolics.Num,
    Ω_range,
    branch::Int64;
    show_progress
) -> Matrix

```

与えられたシステムのヤコビアン応答スペクトルを計算します。指定された周波数範囲にわたる安定解のヤコビアン応答の大きさを計算します。

# 引数

  * `res::Result`: システムの解を含む結果オブジェクト
  * `nat_var::Num`: 応答を評価する自然変数
  * `Ω_range`: 評価する周波数の範囲
  * `branch::Int` または `followed_branches::Vector{Int}`: 分析するブランチ番号
  * `show_progress=true`: 進行状況バーを表示するかどうか
  * `force=false`: すでに存在する場合でもスペクトルの再計算を強制するかどうか

# 戻り値

  * Array{P,2}: 行が周波数に対応し、列が解に対応する複素応答行列
