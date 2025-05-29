```
PureFeedForward <: FeedForwardType
```

純粋フィードフォワード動作を持つコンポーネント出力関数 `g` のトレイト（x に依存しない）：

```
g!(outs..., ins..., p, t)
```

[`FeedForward`](@ref)、[`NoFeedForward`](@ref)、および [`PureStateMap`](@ref) も参照してください。
