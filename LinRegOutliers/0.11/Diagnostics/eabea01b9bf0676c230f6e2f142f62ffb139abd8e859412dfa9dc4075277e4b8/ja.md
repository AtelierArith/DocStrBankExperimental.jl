```
hadimeasure(setting; c = 2.0)
```

与えられた回帰設定に対してハディの回帰診断を適用します

# 引数

  * `setting::RegressionSetting`: 回帰設定オブジェクト。
  * `c::Float64`: 2.0 - 3.0の間で選択された臨界値。デフォルトは2.0です。

# 例

```julia-repl
julia> setting = createRegressionSetting(@formula(calls ~ year), phones);
julia> hadimeasure(setting)
```

# 参考文献

Chatterjee, Samprit and Hadi, Ali. Regression Analysis by Example. 	 5th ed. N.p.: John Wiley & Sons, 2012.
