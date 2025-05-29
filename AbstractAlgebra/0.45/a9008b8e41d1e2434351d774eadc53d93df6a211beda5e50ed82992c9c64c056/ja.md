```
remove(f::T, p::T) where T <: RingElem
```

ペア `v, q` を返します。ここで $p^v$ は $f$ を割る $p$ の最高の冪であり、$q$ はこの冪で $f$ を割った後の共因子です。

また、評価のみを返す [`valuation`](@ref) も参照してください。
