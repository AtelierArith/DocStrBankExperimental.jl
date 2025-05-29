```
EndgameTracker(tracker::Tracker; options = EndgameOptions())
EndgameTracker(H::AbstractHomotopy; options = EndgameOptions())
```

`EndgameTracker`は[`Tracker`](@ref)とエンドゲームを組み合わせたものです。つまり、[`Tracker`](@ref)が解の経路が非特異で収束することを前提とするのに対し、エンドゲームは特異な終点や発散する経路を扱うことを可能にします。特異な解を計算するためには*Cauchyエンドゲーム*が使用され、発散する経路には経路の局所プイセウス級数展開の評価に基づく戦略が使用されます。慣例として、`EndgameTracker`は常に$t=1$から$t=0$まで追跡します。可能なオプションについては[`EndgameOptions`](@ref)を参照してください。
