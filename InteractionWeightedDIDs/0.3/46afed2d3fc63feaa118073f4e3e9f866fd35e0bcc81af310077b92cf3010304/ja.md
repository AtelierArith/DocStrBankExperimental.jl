```
agg(r::RegressionBasedDIDResult{<:DynamicTreatment}, names=nothing; kwargs...)
```

`r`からの係数推定値を、`names`でインデックスされた`r.treatcells`の列からの値によって集約し、各相対時間内で`treatweights`に比例した重みを付けます。

# キーワード

  * `bys=nothing`: `names`でグループ化する前に`r.treatcells`に対する列ごとの変換。
  * `subset=nothing`: 集約に使用される処置係数のサブセット。
