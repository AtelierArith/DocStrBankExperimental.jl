```
struct CU1Irrep <: AbstractIrrep{CU₁}
CU1Irrep(j, s = ifelse(j>zero(j), 2, 0))
Irrep[CU₁](j, s = ifelse(j>zero(j), 2, 0))
```

$$
U₁ ⋊ C
$$

($U₁$ と電荷共役または反射) の群の不変表現を表します。これは単に `O₂` とも呼ばれます。

## フィールド

  * `j::HalfInt`: $U₁$ 電荷の値。
  * `s::Int`: 電荷共役の表現。

これらは次の値を取ることができます：

  * `j == 0` の場合、`s = 0` (自明な電荷共役) または `s = 1` (非自明な電荷共役)
  * `j > 0` の場合、`s = 2` (二次元表現)
