```
charge_trapflt!(samples::AbstractVector{<:RealOrSIMD{<:AbstractFloat}}, navg::Integer, ngap::Integer)
```

`samples` の電荷信号に台形FIRフィルタを適用します。
