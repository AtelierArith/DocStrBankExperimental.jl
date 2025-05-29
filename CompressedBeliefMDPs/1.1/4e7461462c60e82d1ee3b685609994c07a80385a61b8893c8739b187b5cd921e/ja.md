```
compress_POMDP(pomdp, sampler, updater, compressor)
```

与えられたPOMDPから信念をサンプリング、圧縮、キャッシュすることによって、圧縮された信念状態MDPを作成します。

# 引数

  * `pomdp::POMDP`: 圧縮されるPOMDPモデル。
  * `sampler::Sampler`: POMDPから信念のセットを生成するためのサンプラー。
  * `updater::Updater`: 状態から信念を初期化するためのアップデーター。
  * `compressor::Compressor`: 信念の次元を削減するためのコンプレッサー。

# 戻り値

  * `CompressedBeliefMDP`: 構築された圧縮信念状態MDP。
  * `Matrix{Float64}`: 各行がサンプリングされた信念の圧縮表現に対応する行列。

# 使用例

```julia
pomdp = TigerPOMDP() 
sampler = BeliefExpansionSampler(pomdp) 
updater = DiscreteUpdater(pomdp) 
compressor = PCACompressor(2) 
m, B̃ = compress_POMDP(pomdp, sampler, updater, compressor)
```
