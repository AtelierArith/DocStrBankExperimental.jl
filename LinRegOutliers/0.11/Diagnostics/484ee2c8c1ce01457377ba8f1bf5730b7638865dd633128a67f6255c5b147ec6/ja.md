```
jacknifedS(setting, k)
```

k番目の観測値を除外した回帰の標準誤差を推定します。

# 引数

  * `setting::RegressionSetting`: 回帰設定オブジェクト。
  * `k::Int`: 除外される観測値のインデックス。

# 例

```julia-repl
julia> reg = createRegressionSetting(@formula(calls ~ year), phones);
julia> jacknifedS(reg, 2)
57.518441664761035

julia> jacknifedS(reg, 15)
56.14810222161477
```
