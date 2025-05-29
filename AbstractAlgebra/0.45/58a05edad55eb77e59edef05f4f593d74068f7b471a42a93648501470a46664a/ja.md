```
crt(r1::T, m1::T, r2::T, m2::T; check::Bool=true) where T <: RingElement
```

$$
r_1
$$

を$m_1$で、$r_2$を$m_2$で合同な要素を返します。`check = true`の場合、解が存在しないとエラーが発生します。

もし$T$が固定精度整数型（例えば`Int`）であれば、結果は`abs(ri) <= abs(mi)`かつ`abs(m1 * m2) < typemax(T)`であれば正しいです。
