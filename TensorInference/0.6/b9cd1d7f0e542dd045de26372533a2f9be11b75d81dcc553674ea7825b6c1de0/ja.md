```julia
struct RescaledArray{T, N, AT<:AbstractArray{T, N}} <: AbstractArray{T, N}
```

```
RescaledArray(α, T) -> RescaledArray
```

対数前因子を持ち、l∞-正規化されたストレージを持つ配列データ型、すなわちテンソル内の最大要素は1です。このテンソル型は、テンソネットワーク内の数値の潜在的なアンダーフロー/オーバーフローを回避できます。コンストラクタ `RescaledArray(α, T)` は、`exp(α) * T` に等しい再スケーリングされた配列を作成します。
