```
BeliefExpansionSampler
```

探索的信念拡張の高速拡張（[意思決定のためのアルゴリズム](https://algorithmsbook.com/)のアルゴリズム21.13）で、$k$-dツリーを使用します。

## フィールド

  * `updater::Updater`: 信念を更新するために使用されるアップデーター。
  * `metric::NearestNeighbors.MinkowskiMetric`: 信念間の距離を測定するために使用されるメトリック。

これは[Minkowskiメトリック](https://en.wikipedia.org/wiki/Minkowski_distance)でなければなりません。

  * `n::Integer`: 実行する信念拡張の数。

## コンストラクタ

```
BeliefExpansionSampler(pomdp::POMDP; updater::Updater=DiscreteUpdater(pomdp),
metric::NearestNeighbors.MinkowskiMetric=Euclidean(), n::Integer=3)
```

## メソッド

```
(s::BeliefExpansionSampler)(pomdp::POMDP)
```

初期信念を作成し、探索的信念拡張を実行します。ユニークな信念状態を返します。離散状態、アクション、および観測空間を持つPOMDPにのみ機能します。

## 使用例

```julia-repl
julia> pomdp = TigerPOMDP();
julia> sampler = BeliefExpansionSampler(pomdp; n=2);
julia> beliefs = sampler(pomdp)
Set{DiscreteBelief{TigerPOMDP, Bool}} with 4 elements:
  DiscreteBelief{TigerPOMDP, Bool}(TigerPOMDP(-1.0, -100.0, 10.0, 0.85, 0.95), Bool[0, 1], [0.15000000000000002, 0.85])
  DiscreteBelief{TigerPOMDP, Bool}(TigerPOMDP(-1.0, -100.0, 10.0, 0.85, 0.95), Bool[0, 1], [0.5, 0.5])
  DiscreteBelief{TigerPOMDP, Bool}(TigerPOMDP(-1.0, -100.0, 10.0, 0.85, 0.95), Bool[0, 1], [0.85, 0.15000000000000002])
  DiscreteBelief{TigerPOMDP, Bool}(TigerPOMDP(-1.0, -100.0, 10.0, 0.85, 0.95), Bool[0, 1], [0.9697986577181208, 0.030201342281879207])
```
