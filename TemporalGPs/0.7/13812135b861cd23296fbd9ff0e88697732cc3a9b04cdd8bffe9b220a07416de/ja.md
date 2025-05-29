```
RegularSpacing{T<:Real} <: AbstractVector{T}
```

`RegularSpacing(t0, Δt, N)` は `range(t0; step=Δt, length=N)` と同じものを表しますが、拡張精度浮動小数点数を使用しない異なる実装を持っています。これはすべてのADフレームワークに必要です。
