```
sum_fast(s::AbstractSmallSet{N,T}) where {N,T}
```

`s`の要素の`@fastmath`合計を返します。`sum`とは異なり、戻り値は常に`s`の要素型になります。小さなビット整数の場合でも同様です。

`Base.sum`、`Base.@fastmath`も参照してください。
