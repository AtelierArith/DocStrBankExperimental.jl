```
pwcoverage(lb::AbstractVector, ub::AbstractVector, draws::AbstractMatrix)
```

ブートストラップ `draws` における点推定値のうち、各パラメータごとに対応する信頼区間の下限 `lb` と上限 `ub` によってカバーされている割合を計算します。詳細は [`simulcoverage`](@ref) を参照してください。
