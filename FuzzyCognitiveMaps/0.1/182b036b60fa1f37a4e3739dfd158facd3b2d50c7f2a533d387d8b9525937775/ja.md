```
    create_fcm(;
csv_file::Union{String, Nothing}=nothing,
concepts::Vector{String}=String[],
weights::Matrix{Float64}=Matrix{Float64}(undef, 0, 0),
activation::Function=sigmoid,
initial_state::Union{Vector{Float64}, Nothing}=nothing,
track_history::Bool=false,
external_concepts::Union{Vector{Bool}, Nothing}=nothing)
```

CSVファイルからファジー認知マップ（FCM）を作成します。

# 引数

  * `csv_file::Union{String, Nothing}`: FCMデータを含むCSVファイルへのパス。
  * `concepts::Vector{String}`: FCM内の概念の名前。
  * `weights::Matrix{Float64}`: 概念間の接続の重み。
  * `activation::Function`: FCMの活性化関数。
  * `initial_state::Union{Vector{Float64}, Nothing}`: 概念の初期状態。
  * `track_history::Bool`: 各イテレーションでFCMの状態を追跡するかどうか。
  * `external_concepts::Union{Vector{Bool}, Nothing}`: 概念が外部であるかどうか。
