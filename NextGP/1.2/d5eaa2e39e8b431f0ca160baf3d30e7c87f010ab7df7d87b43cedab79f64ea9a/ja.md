```
    function BayesC(pi,v;estimatePi=false)
```

  * `pi` は各 McMC サイクルでモデルに含める SNP の割合です。`estimatePi=true` の場合、これは開始値としてのみ使用されます。
  * `v` は SNP の事前分布の分散です。
  * `estimatePi` は `pi` が推定される場合は `true` です。デフォルトでは `false` です。
