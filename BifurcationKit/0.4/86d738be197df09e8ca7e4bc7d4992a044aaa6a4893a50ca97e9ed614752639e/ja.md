```julia
struct PairOfEvents{Tc<:BifurcationKit.AbstractContinuousEvent, Td<:BifurcationKit.AbstractDiscreteEvent} <: BifurcationKit.AbstractEvent
```

継続アルゴリズムにPairOfEvents関数を渡すための構造体です。これは、ContinuousEvent / DiscreteEventのペアで構成されています。`PairOfEvents`は、コンストラクタに`ContinuousEvent`と`DiscreteEvent`を渡すことで構築されます：

```
PairOfEvents(contEvent, discreteEvent)
```

## フィールド

  * `eventC::BifurcationKit.AbstractContinuousEvent`: 連続イベント
  * `eventD::BifurcationKit.AbstractDiscreteEvent`: 離散イベント
