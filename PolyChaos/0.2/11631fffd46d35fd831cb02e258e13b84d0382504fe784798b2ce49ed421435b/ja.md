```
quadgp(weight::Function,lb::Real,ub::Real,N::Int=10;quadrature::Function=clenshaw_curtis,bnd::Float64=Inf)
```

ガウチの「直交多項式：計算と近似」、セクション2.2.2、pp. 93-95に基づく一般目的の数値積分

サポート（`lb`、`ub`）を持つ`weight`のための`N`点数値積分ルールを計算します。数値積分ルールはキーワード`quadrature`で指定できます。キーワード`bnd`は無限大の数値値を設定します。
