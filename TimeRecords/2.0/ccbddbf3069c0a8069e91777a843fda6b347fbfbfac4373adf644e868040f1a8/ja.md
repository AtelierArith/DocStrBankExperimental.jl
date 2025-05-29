```
interpolate(f_interp::Function, ts::AbstractTimeSeries, t::Real, indhint::Union{Nothing,Integer,<:RefValue{<:Integer}})
```

時刻 t::Real における単一外挿、より速い検索のために indhint を提供します
