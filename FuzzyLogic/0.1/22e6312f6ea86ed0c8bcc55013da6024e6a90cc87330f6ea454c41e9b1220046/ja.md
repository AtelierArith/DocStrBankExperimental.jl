```julia
struct Type2MF{MF1<:FuzzyLogic.AbstractMembershipFunction, MF2<:FuzzyLogic.AbstractMembershipFunction} <: FuzzyLogic.AbstractMembershipFunction
```

タイプ2メンバーシップ関数。

  * `lo::FuzzyLogic.AbstractMembershipFunction`: 下限メンバーシップ関数。
  * `hi::FuzzyLogic.AbstractMembershipFunction`: 上限メンバーシップ関数。

### 例

```julia
mf = 0.7 * TriangularMF(3, 5, 7) .. TriangularMF(1, 5, 9)
```
