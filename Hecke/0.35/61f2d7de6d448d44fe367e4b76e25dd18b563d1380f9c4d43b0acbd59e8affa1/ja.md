```
ideal(O::RelNumFieldOrder{T, S}, x::RelNumFieldOrderElem{T}) -> RelNumFieldOrderIdeal{T, S}
*(O::RelNumFieldOrder{T, S}, x::RelNumFieldOrderElem{T}) -> RelNumFieldOrderIdeal{T, S}
*(x::RelNumFieldOrderElem{T}, O::RelNumFieldOrder{T, S}) -> RelNumFieldOrderIdeal{T, S}
```

$$
\mathcal O
$$

の理想$x\cdot \mathcal O$を作成します。
