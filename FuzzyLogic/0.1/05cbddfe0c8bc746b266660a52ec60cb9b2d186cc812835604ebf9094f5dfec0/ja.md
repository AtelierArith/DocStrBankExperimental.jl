```julia
struct LeftMaximumDefuzzifier <: FuzzyLogic.AbstractDefuzzifier
```

左最大デファジファイザ。メンバーシップ関数が最大値に達するドメイン内の最小値を返します。

### パラメータ

  * `N::Int64`: サブ区間の数、デフォルトは100。
  * `tol::Float64`: 値が最大かどうかを判断するための絶対許容誤差、デフォルトは `eps(Float64)`。
