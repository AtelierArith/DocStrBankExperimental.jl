```
(bucket::NeuralBucket)(input::AbstractArray{T,3}, pas::ComponentVector; kwargs...) where {T,N}
```

入力データに神経バケットモデルを適用して、水のフラックスと時間にわたる状態の更新を計算します。

# 引数

  * `input::AbstractArray{T,3}`: 形状 (variables, nodes, timesteps) の入力データ配列。
  * `pas::ComponentVector`: 通常のパラメータと初期状態の両方を含むモデルパラメータ。
  * `kwargs`: 追加のキーワード引数：

      * `ptyidx::AbstractVector{Int}`: 分散実行のためのパラメータタイプインデックス (デフォルト: すべてのノード)。
      * `styidx::AbstractVector{Int}`: 分散実行のための状態タイプインデックス (デフォルト: すべてのノード)。
      * `initstates::ComponentVector`: 初期状態の値 (デフォルト: すべての状態に対してゼロ)。

# 戻り値

  * `Array{T,3}`: 形状 (output_variables, nodes, timesteps) の出力配列。

# 説明

この関数は、神経バケットの再帰モデルを入力の時系列データに適用し、分散（マルチノード）シミュレーションをサポートします。この関数は、再帰ニューラルネットワークアーキテクチャを通じて内部的に状態の更新を処理します。

入力配列は、最初の次元に変数、2番目の次元にノード、3番目の次元に時間ステップが配置されている必要があります。
