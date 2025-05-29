```
simulcoverage(lb::AbstractVector, ub::AbstractVector, draws::AbstractMatrix, nuncovered=0)
```

ブートストラップ `draws` において、下限 `lb` と上限 `ub` の信頼区間に同時に含まれる点推定の割合を計算します。ただし、最大で `nuncovered` パラメータは除外されます。詳細は [`pwcoverage`](@ref) を参照してください。
