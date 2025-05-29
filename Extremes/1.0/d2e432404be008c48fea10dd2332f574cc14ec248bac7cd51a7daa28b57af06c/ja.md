```
quantile(fm::pwmAbstractExtremeValueModel, p::Real)::Vector{<:Real}
```

フィッティングされたモデルからレベル `p` の分位数を計算します。確率加重モーメント法では、モデルは定常でなければなりません。
