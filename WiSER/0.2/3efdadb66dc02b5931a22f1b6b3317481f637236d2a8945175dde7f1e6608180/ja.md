```
init_ls!(m::WSVarLmmModel; gniters::Integer = 5)
```

`WSVarLmmModel`オブジェクトのパラメータを最小二乗推定から初期化します。 `m.β` は `inv(sum(xi'xi)) * sum(xi'yi)` に初期化されます。 `m.Σγ` は `inv(sum(zi'zi⊗zi'zi)) * sum(zi'ri⊗zi'ri)` に初期化されます。 `m.τ` は `inv(sum(wi'wi)) * sum(wi'log(abs2(ri)))` に初期化されます。 `gniters > 0` の場合、τを改善するために `gniters` 回のガウス・ニュートン反復を実行します。
