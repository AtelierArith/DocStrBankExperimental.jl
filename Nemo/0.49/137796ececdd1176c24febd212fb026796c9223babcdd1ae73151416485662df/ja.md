```
powermod(x::ZZRingElem, p::Int, m::ZZRingElem)
```

$$
x^p (\mod m)
$$

を返します。余りは範囲 $[0, m)$ にあります。
