```julia
struct ProductSigmoidMF{T<:Real} <: FuzzyLogic.AbstractMembershipFunction
```

二つのシグモイドの積。詳細は [`SigmoidMF`](@ref) を参照してください。

### フィールド

  * `a1::Real`: 最初のシグモイドの傾き。
  * `c1::Real`: 最初のシグモイドの中心。
  * `a2::Real`: 二番目のシグモイドの傾き。
  * `c2::Real`: 二番目のシグモイドの中心。

### 例

```julia
mf = ProductSigmoidMF(2, 3, -5, 8)
```
