```
std_error(obs::Observable[; method=:full])
```

平均の標準誤差を推定します。ビン分析を通じて測定間の相関を考慮します。

オプションの `method` キーワードは `:log`、`:full`、または `:jackknife` です。

また、[`mean(obs)`](@ref) も参照してください。
