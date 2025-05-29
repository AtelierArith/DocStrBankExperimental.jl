```julia
struct SigmoidMF{T<:Real} <: FuzzyLogic.AbstractMembershipFunction
```

シグモイドメンバーシップ関数 $\frac{1}{1+e^{-a(x-c)}}$。

### フィールド

  * `a::Real`: 曲線の傾きを制御するパラメータ。
  * `c::Real`: 傾きの中心。

### 例

```julia
mf = SigmoidMF(2, 5)
```
