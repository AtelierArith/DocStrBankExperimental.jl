```
demo_pendcart(;kwargs...)
```

"カート上の振り子システム"の最適軌道を見つけるためにiLQG関数を実行します。パッケージControlSystems.jlが必要です。

# 引数

`x0     = [π-0.6,0,0,0]` `goal   = [π,0,0,0]` `Q      = Diagonal([10,1,2,1])` : 状態重み行列 `R      = 1`                    : 制御重み行列 `lims   = 5.0*[-1 1]`           : 制御制限, `T      = 600`                  : 時間ステップ数 `doplot = true`                 : 結果をプロットする
