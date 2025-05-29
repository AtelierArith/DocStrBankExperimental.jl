```
dffit(setting, i)
```

ith観測値が線形回帰フィットに与える影響を計算します。

# 引数

  * `setting::RegressionSetting`: 回帰設定オブジェクト。
  * `i::Int`: 観測値のインデックス。

# 例

```julia-repl
julia> reg = createRegressionSetting(@formula(calls ~ year), phones);
julia> dffit(reg, 1)
2.3008326745719785

julia> dffit(reg, 15)
2.7880619386124295

julia> dffit(reg, 16)
3.1116532421969794

julia> dffit(reg, 17)
4.367981450347031

julia> dffit(reg, 21)
-5.81610150322166
```

# 参考文献

Belsley, David A., Edwin Kuh, and Roy E. Welsch. Regression diagnostics:  Identifying influential data and sources of collinearity. Vol. 571. John Wiley & Sons, 2005.
