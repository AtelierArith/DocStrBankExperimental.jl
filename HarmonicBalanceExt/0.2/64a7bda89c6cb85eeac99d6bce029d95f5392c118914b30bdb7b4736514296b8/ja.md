```julia
get_linear_response(
    res::HarmonicSteadyState.Result{D, S, P, F} where F<:FunctionWrappers.FunctionWrapper{Array{S, 2}, Tuple{Array{S, 1}}},
    nat_var::Symbolics.Num,
    Ω_range,
    branch::Int64;
    show_progress
) -> Matrix

```

システムの線形応答を指定されたブランチに対して計算します。指定された範囲内の各安定解および入力周波数に対して線形応答ODEを解くことによって線形応答を評価します。

# 引数

  * `res`: システムの解を含む結果オブジェクト
  * `nat_var::Num`: 応答を評価する自然変数
  * `Ω_range`: 評価する周波数の範囲
  * `branch::Int`: 分析するブランチ番号
  * `show_progress=true`: 進行状況バーを表示するかどうか

# 戻り値

  * Array{P,2}: 行が周波数に対応し、列が安定解に対応する応答行列
