```
NoFeedForward <: FeedForwardType
```

フィードフォワード動作がないコンポーネント出力関数 `g` のためのトレイト（入力に依存しない）：

```
g!(outs..., x, p, t)
```

[`PureFeedForward`](@ref)、[`FeedForward`](@ref)、および [`PureStateMap`](@ref) も参照してください。
