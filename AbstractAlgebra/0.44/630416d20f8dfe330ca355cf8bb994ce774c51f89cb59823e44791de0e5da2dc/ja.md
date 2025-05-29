```
remove(z::MPolyRingElem{T}, p::MPolyRingElem{T}) where {T <: RingElement}
```

$$
z
$$

の$p$における評価を計算します。つまり、$p^k$が$z$を割り切る最大の$k$を求めます。さらに、$z/p^k$が2つ目の戻り値として返されます。

また、評価のみを返す`valuation`も参照してください。
