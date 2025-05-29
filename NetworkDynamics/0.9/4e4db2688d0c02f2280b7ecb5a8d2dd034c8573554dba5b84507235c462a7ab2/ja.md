```
FeedForward <: FeedForwardType
```

フィードフォワード動作を持つコンポーネント出力関数 `g` のためのトレイト。すべてに依存する可能性があります：

```
g!(outs..., x, ins..., p, t)
```

[`PureFeedForward`](@ref)、[`NoFeedForward`](@ref)、および [`PureStateMap`](@ref) も参照してください。
