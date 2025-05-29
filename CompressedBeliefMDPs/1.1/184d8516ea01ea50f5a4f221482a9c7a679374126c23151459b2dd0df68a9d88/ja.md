```
PolicySampler
```

ポリシーを展開することによって信念状態をサンプリングします。

## フィールド

  * `policy::Policy`: 意思決定に使用されるポリシー。
  * `updater::Updater`: 信念を更新するために使用されるアップデーター。
  * `n::Integer`: シミュレーションされたステップの最大数。
  * `rng::AbstractRNG`: サンプリングに使用される乱数生成器。
  * `verbose::Bool`: サンプリング中にプログレスバーを使用するかどうか。

## コンストラクタ

```
PolicySampler(pomdp::POMDP; policy::Policy=RandomPolicy(pomdp), 
updater::Updater=DiscreteUpdater(pomdp), n::Integer=10, 
rng::AbstractRNG=Random.GLOBAL_RNG)
```

## メソッド

```
(s::PolicySampler)(pomdp::POMDP)
```

*ユニーク*な信念状態のベクターを返します。

# 例

```julia-repl
julia> pomdp = TigerPOMDP();
julia> sampler = PolicySampler(pomdp; n=3); 
julia> 2-element Vector{Any}:
DiscreteBelief{TigerPOMDP, Bool}(TigerPOMDP(-1.0, -100.0, 10.0, 0.85, 0.95), Bool[0, 1], [0.5, 0.5])
DiscreteBelief{TigerPOMDP, Bool}(TigerPOMDP(-1.0, -100.0, 10.0, 0.85, 0.95), Bool[0, 1], [0.15000000000000002, 0.85])
```
