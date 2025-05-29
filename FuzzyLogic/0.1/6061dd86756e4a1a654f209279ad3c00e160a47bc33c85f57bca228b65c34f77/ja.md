```julia
struct MeanOfMaximaDefuzzifier <: FuzzyLogic.AbstractDefuzzifier
```

最大値の平均デファジファイア。メンバーシップ関数が最大に達するドメイン内の値の平均を返します。

### パラメータ

  * `N::Int64`: サブインターバルの数、デフォルトは100。
  * `tol::Float64`: 値が最大かどうかを判断するための絶対許容誤差、デフォルトは `eps(Float64)`。
