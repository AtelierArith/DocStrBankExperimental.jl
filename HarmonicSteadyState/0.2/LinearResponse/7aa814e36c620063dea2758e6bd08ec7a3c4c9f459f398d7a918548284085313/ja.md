```julia
get_rotframe_jacobian_response(
    res::HarmonicSteadyState.Result{D, S, P, F} where F<:FunctionWrappers.FunctionWrapper{Array{S, 2}, Tuple{Array{S, 1}}},
    Ω_range,
    branch::Int64;
    show_progress,
    damping_mod
)

```

与えられたブランチの回転フレームヤコビアン応答を計算します。数値ヤコビアンの固有値を評価し、範囲内の各周波数に対する応答の大きさを計算することによって、回転フレームヤコビアン応答を計算します。

# 引数

  * `res::Result`: システムの解を含む結果オブジェクト
  * `Ω_range`: 評価する周波数の範囲
  * `branch::Int`: 分析するブランチ番号
  * `show_progress=true`: 進行状況バーを表示するかどうか
  * `damping_mod`: 減衰修正パラメータ

# 戻り値

  * Array{P,2}: 回転フレーム内の応答行列
