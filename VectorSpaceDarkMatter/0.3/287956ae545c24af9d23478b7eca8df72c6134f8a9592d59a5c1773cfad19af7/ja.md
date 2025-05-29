```
readFnlm(infile[, radial_basis::RadialBasis]; dict=false, use_err=true)
```

`infile` から係数を読み込みます。オプションで `radial_basis` 引数を介して基底を手動で定義できます。オプションの引数：

`dict` : `true` の場合、`FCoeffs` を返します。false の場合、`ProjectedF` を返します。

`use_err` : `fnlm` 値の不確実性を読み込むかどうか。
