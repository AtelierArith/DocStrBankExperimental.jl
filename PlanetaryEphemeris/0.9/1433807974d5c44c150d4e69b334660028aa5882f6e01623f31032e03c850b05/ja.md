```
selecteph(eph::TaylorInterpolant, bodyind::Union{Int, AbstractVector{Int}}, t0::T = eph.t0,
          tf::T = eph.t0 + eph.t[end]; euler::Bool = false, ttmtdb::Bool = false) where {T <: Real}
```

`eph`のサブセットを返し、`bodyind`の天体のエフェメリスのみをタイムレンジ`[t0, tf]`で取得します。キーワード引数を使用すると、月のオイラー角および/またはTT-TDBを含めることができます。
