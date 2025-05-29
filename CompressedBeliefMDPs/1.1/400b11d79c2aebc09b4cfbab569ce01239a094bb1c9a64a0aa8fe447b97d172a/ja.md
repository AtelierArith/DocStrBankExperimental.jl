```
ExplorationPolicySampler
```

`ExplorationPolicy`を展開することで信念状態をサンプリングします。基本的には`PolicySampler`と同じです。

## フィールド

  * `explorer::ExplorationPolicy`: 意思決定に使用される`ExplorationPolicy`。
  * `on_policy::Policy`: 探索していないときに意思決定に使用されるフォールバック`Policy`。
  * `updater::Updater`: 信念を更新するために使用されるアップデーター。
  * `n::Integer`: シミュレーションされたステップの最大数。
  * `rng::AbstractRNG`: サンプリングに使用される乱数生成器。
  * `verbose::Bool`: サンプリング中にプログレスバーを使用するかどうか。

## コンストラクタ

```
ExplorationPolicySampler(pomdp::POMDP; rng::AbstractRNG=Random.GLOBAL_RNG,
explorer::ExplorationPolicy=EpsGreedyPolicy(pomdp, 0.1; rng=rng), on_policy=RandomPolicy(pomdp),
updater::Updater=DiscreteUpdater(pomdp), n::Integer=10)
```

## メソッド

```
(s::ExplorationPolicySampler)(pomdp::POMDP)
```

*ユニーク*な信念状態のベクターを返します。

## 使用例

```julia-repl
julia> pomdp = TigerPOMDP()
julia> sampler = ExplorationPolicySampler(pomdp; n=30)
julia> sampler(pomdp)
3-element Vector{Any}:
 DiscreteBelief{TigerPOMDP, Bool}(TigerPOMDP(-1.0, -100.0, 10.0, 0.85, 0.95), Bool[0, 1], [0.5, 0.5])
 DiscreteBelief{TigerPOMDP, Bool}(TigerPOMDP(-1.0, -100.0, 10.0, 0.85, 0.95), Bool[0, 1], [0.85, 0.15000000000000002])
 DiscreteBelief{TigerPOMDP, Bool}(TigerPOMDP(-1.0, -100.0, 10.0, 0.85, 0.95), Bool[0, 1], [0.9697986577181208, 0.030201342281879207])
```
