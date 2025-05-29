```
designMatrix(setting)

与えられた回帰設定の定数項の変数（1の列）を含む独立変数の行列を返します。
```

# 引数

  * `setting::RegressionSetting`: 回帰設定オブジェクト。

# 注意事項

```
デザイン行列は、与えられた線形回帰モデルの独立変数の値を列に保持する行列です。
```

# 例

```julia-repl
julia> setting = createRegressionSetting(@formula(calls ~ year), phones);
julia> designMatrix(setting)
24×2 Matrix{Float64}:
 1.0  50.0
 1.0  51.0
 1.0  52.0
 1.0  53.0
 1.0  54.0
 1.0  55.0
 1.0  56.0
 1.0  57.0
 1.0  58.0
 1.0  59.0
 1.0  60.0
 1.0  61.0
 1.0  62.0
 1.0  63.0
 1.0  64.0
 1.0  65.0
 1.0  66.0
 1.0  67.0
 1.0  68.0
 1.0  69.0
 1.0  70.0
 1.0  71.0
 1.0  72.0
 1.0  73.0
```
