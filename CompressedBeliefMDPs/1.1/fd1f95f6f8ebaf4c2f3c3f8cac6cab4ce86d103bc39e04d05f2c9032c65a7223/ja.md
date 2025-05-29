```
CompressedBeliefMDP{B, A}
```

`CompressedBeliefMDP`構造体は、[Exponential Family PCA for Belief Compression in POMDPs](https://papers.nips.cc/paper_files/paper/2002/hash/a11f9e533f28593768ebf87075ab34f2-Abstract.html)で提示された圧縮信念状態MDPの一般化です。

## 型パラメータ

  * `B`: 圧縮信念状態の型。
  * `A`: 行動の型。

## フィールド

  * `bmdp::GenerativeBeliefMDP`: 生成的信念状態MDP。
  * `compressor::Compressor`: 信念状態を圧縮するために使用される圧縮器。
  * `ϕ::Bijection`: 非圧縮信念状態から圧縮信念状態へのマッピングを表す双射。詳細はノートを参照。

## コンストラクタ

```
CompressedBeliefMDP(pomdp::POMDP, updater::Updater, compressor::Compressor)
CompressedBeliefMDP(pomdp::POMDP, sampler::Sampler, updater::Updater, compressor::Compressor)
```

指定されたPOMDP、アップデーター、および圧縮器を使用して`CompressedBeliefMDP`を構築します。

!!! warning
    4引数のコンストラクタは、与えられた圧縮器に対して[`fit!`](@ref)を呼び出す生活の質向上のためのコンストラクタです。


## 使用例

```julia
pomdp = TigerPOMDP()
updater = DiscreteUpdater(pomdp)
compressor = PCACompressor(1)
mdp = CompressedBeliefMDP(pomdp, updater, compressor)
```

連続POMDPについては、[ParticleFilters.jl](https://juliapomdp.github.io/ParticleFilters.jl/latest/basic/)を参照してください。

## ノート

  * 圧縮は通常単射ではありませんが、信念とその圧縮を先着順でキャッシュするため、一般性を失うことなく双射を効果的に使用できます。
