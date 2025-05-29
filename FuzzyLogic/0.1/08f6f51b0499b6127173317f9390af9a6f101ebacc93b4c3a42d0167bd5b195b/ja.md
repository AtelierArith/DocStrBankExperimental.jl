```julia
struct DifferenceSigmoidMF{T<:Real} <: FuzzyLogic.AbstractMembershipFunction
```

二つのシグモイドの差。詳細は[`SigmoidMF`](@ref)を参照。

### フィールド

  * `a1::Real`: 最初のシグモイドの傾き。
  * `c1::Real`: 最初のシグモイドの中心。
  * `a2::Real`: 二つ目のシグモイドの傾き。
  * `c2::Real`: 二つ目のシグモイドの中心。

### 例

```julia
mf = DifferenceSigmoidMF(5, 2, 5, 7)
```
