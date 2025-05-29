```
valuation(z::MPolyRingElem{T}, p::MPolyRingElem{T}) where {T <: RingElement}
```

$$
z
$$

の$p$における評価を計算します。つまり、$p^k$が$z$を割り切る最大の$k$を求めます。

また、$z/p^k$を返す`remove`も参照してください。
