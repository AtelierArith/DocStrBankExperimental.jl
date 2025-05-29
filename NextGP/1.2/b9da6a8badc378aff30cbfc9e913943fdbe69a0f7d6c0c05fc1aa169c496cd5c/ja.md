```
    function BayesLV(v,f,covariates,zeta)
```

  * `v` は SNP の事前分布の分散です。
  * `f` は分散のモデル式です。
  * `covariates` は各 SNP の分散に対する説明変数を含む `DataFrame` です。
  * `zeta` は SNP の分散に対するモデルの誤差分散です。
  * `estimateVarZeta` が `true` の場合、SNP の分散に対するモデルの誤差分散は対数分散の分散の 0.01 パーセントであると仮定します。`estimateVarZeta` が `false` の場合、対数線形分散の誤差分散として `zeta` を使用します（固定値）。`estimateVarZeta` が `Float64` の場合、SNP の分散に対するモデルの誤差分散は対数分散の分散の `estimateVarZeta` パーセントであると仮定します。
