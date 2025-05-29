```
create_fcm(concepts::Vector{String}, weights::Matrix{Float64},
           activation::Function, initial_state::Vector{Float64};
           track_history::Bool=false,
           external_concepts::Vector{Bool}=falses(length(concepts)))
```

指定されたパラメータで新しいファジー認知マップ（FCM）を作成します。

# 引数

  * `concepts::Vector{String}`: FCM内の概念の名前
  * `weights::Matrix{Float64}`: 概念間の因果重みを表す隣接行列
  * `activation::Function`: 状態更新中に適用される活性化関数
  * `initial_state::Vector{Float64}`: 各概念の初期活性化値
  * `track_history::Bool=false`: 更新中に状態履歴を追跡するかどうか
  * `external_concepts::Vector{Bool}`: どの概念が外部（更新中に固定）であるかを示す

# 戻り値

  * `FuzzyCognitiveMap`: 指定されたパラメータで初期化された新しいFCMインスタンス
