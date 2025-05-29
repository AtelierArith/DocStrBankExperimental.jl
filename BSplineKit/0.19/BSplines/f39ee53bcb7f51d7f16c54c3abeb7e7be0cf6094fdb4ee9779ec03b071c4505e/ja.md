```
PeriodicKnots{T} <: AbstractVector{T}
```

周期性 `L` を持つノットの無限ベクトルを表します。

---

```
PeriodicKnots(ξs::AbstractVector{T}, ::BSplineOrder{k})
```

ブレークポイント `ξs` から周期的なノット列を構築します。

ノットの周期は `L = ξs[end] - ξs[begin]` として取られます。言い換えれば、ブレークポイント `ξs` は端点 `ξs[begin] + L` を含むことが期待されます。

ブレークポイントは非減少順に与えられるべきです。

返されるノット `ts` のインデックスは、入力 `ξs` に対してオフセットされており、`ts[i] = ξs[i + offset]` という関係があります。ここで、`offset = k ÷ 2` です。
