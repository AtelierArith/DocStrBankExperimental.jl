```
 track(tracker::Tracker, x::AbstractVector, t₁ = 1.0, t₀ = 0.0; debug::Bool = false)
```

与えられた解 `x` を `t₁` で `tracker` を使用して `t₀` での解に追跡します。

```
track(tracker::Tracker, r::TrackerResult, t₁ = 1.0, t₀ = 0.0; debug::Bool = false)
```

結果 `r` の解を `t₁` から `t₀` まで追跡します。
