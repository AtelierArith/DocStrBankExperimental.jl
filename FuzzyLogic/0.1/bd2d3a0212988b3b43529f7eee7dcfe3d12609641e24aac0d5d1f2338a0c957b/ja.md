```julia
struct WeightedMF{MF<:FuzzyLogic.AbstractMembershipFunction, T<:Real} <: FuzzyLogic.AbstractMembershipFunction
```

パラメータ $0 ≤ w ≤ 1$ でスケーリングされたメンバーシップ関数。

  * `mf::FuzzyLogic.AbstractMembershipFunction`: メンバーシップ関数。
  * `w::Real`: スケーリングファクター。

### 例

```julia
mf = 0.5 * TriangularMF(1, 2, 3)
```
