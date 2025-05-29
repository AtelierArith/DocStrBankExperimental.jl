```
track!(tracker::Tracker, x, t₁ = 1.0, t₀ = 0.0; debug::Bool = false)
```

[`track`](@ref)と同じですが、最終的な[`TrackerCode`](@ref)のみを返します。

```
track!(tracker::Tracker, t₀; debug::Bool = false)
```

`tracker`を使用して、現在の解を`t₀`まで追跡します。これにより、現在の状態が保持されます。
