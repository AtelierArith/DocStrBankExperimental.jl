```
crt_with_lcm(r1::T, m1::T, r2::T, m2::T; check::Bool=true) where T <: RingElement
```

$$
m_1
$$

と$m_2$の最小公倍数と、$r_1$が$m_1$で、$r_2$が$m_2$で合同な要素からなるタプルを返します。`check = true`の場合、解が存在しないときはエラーが発生します。
