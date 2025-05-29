```
responseVector(setting)

与えられた回帰設定の従属変数のベクトルを返します。
```

# 引数

  * `setting::RegressionSetting`: 回帰設定オブジェクト。

# 例

```julia-repl
julia> setting = createRegressionSetting(@formula(calls ~ year), phones);
julia> responseVector(setting)
24-element Vector{Float64}:
   4.4
   4.7
   4.7
   5.9
   6.6
   7.3
   8.1
   8.8
  10.6
  12.0
  13.5
  14.9
  16.1
  21.2
 119.0
 124.0
 142.0
 159.0
 182.0
 212.0
  43.0
  24.0
  27.0
  29.0
```
