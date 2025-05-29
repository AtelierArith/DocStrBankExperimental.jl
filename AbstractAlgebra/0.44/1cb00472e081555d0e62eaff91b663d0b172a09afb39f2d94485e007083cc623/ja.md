```
crt_with_lcm(r1::T, m1::T, r2::T, m2::T; check::Bool=true) where T <: RingElement
```

$$
m_1
$$

と$m_2$の最小公倍数と、$m_1$で$r_1$と合同であり、$m_2$で$r_2$と合同である要素からなるタプルを返します。`check = true`の場合、解が存在しないときはエラーが発生します。
