```julia
struct SingletonMF{T<:Real} <: FuzzyLogic.AbstractMembershipFunction
```

シングルトンメンバーシップ関数。単一の点で1に等しく、他の場所では0です。

### フィールド

  * `c::Real`: メンバーシップ関数が値1を持つ点。

### 例

```julia
mf = SingletonMF(4)
```
