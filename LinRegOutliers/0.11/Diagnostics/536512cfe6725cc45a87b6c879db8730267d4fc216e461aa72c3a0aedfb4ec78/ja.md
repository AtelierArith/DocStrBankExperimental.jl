```
hatmatrix(setting)
```

与えられた回帰設定に対して、n の観測値を持つ n x n のハット行列を計算します。

# 引数

  * `setting::RegressionSetting`: 回帰設定オブジェクト。

# 例

```julia-repl
julia> reg = createRegressionSetting(@formula(calls ~ year), phones);
julia> size(hatmatrix(reg))

(24, 24)
```
