```julia
struct RightMaximumDefuzzifier <: FuzzyLogic.AbstractDefuzzifier
```

右最大デファジファイザ。メンバーシップ関数が最大値に達するドメイン内の最大値を返します。

### パラメータ

  * `N::Int64`: サブインターバルの数、デフォルトは100。
  * `tol::Float64`: 値が最大であるかどうかを判断するための絶対許容誤差、デフォルトは `eps(Float64)`。
