```
powermod(x::ZZRingElem, p::ZZRingElem, m::ZZRingElem)
```

$$
x^p (\mod m)
$$

を返します。余りは $[0, m)$ の範囲になります。
