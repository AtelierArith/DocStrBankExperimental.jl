```julia
struct SetOfEvents{Tc<:Tuple, Td<:Tuple} <: BifurcationKit.AbstractEvent
```

複数のイベントを連結して `SetOfEvents` を形成することができます。`SetOfEvents` は、コンストラクタ `ContinuousEvent`、`DiscreteEvent` または他の `SetOfEvents` インスタンスを渡すことによって構築されます：

```
SetOfEvents(cb1, cb2, cb3)
```

# 例

```
 BifurcationKit.SetOfEvents(BK.FoldDetectCB, BK.BifDetectCB)
```

好きなだけイベントを渡すことができます。

  * `eventC::Tuple`: 連続イベント
  * `eventD::Tuple`: 離散イベント
