```julia
struct GaussianMF{T<:Real} <: FuzzyLogic.AbstractMembershipFunction
```

ガウス会員関数 $e^{-\frac{(x-μ)²}{2σ²}}$。

### フィールド

  * `mu::Real`: 平均 $μ$。
  * `sig::Real`: 標準偏差 $σ$。

### 例

```julia
mf = GaussianMF(5.0, 1.5)
```
