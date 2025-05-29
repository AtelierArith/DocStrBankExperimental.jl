```
galts(setting)
```

LTS係数を推定するためのSatman(2012)アルゴリズムを実行します。

# 引数

  * `setting`: 回帰設定オブジェクト。

# 説明

このアルゴリズムは、Cステップを使用してLTS係数を推定するための遺伝的探索を実行します。

# 出力

  * `["betas"]`: ロバスト回帰係数
  * `["best.subset"]`: hの観測値のクリーンなサブセット。ここで、hはn / 2より大きい整数です。hのデフォルト値は`Int(floor((n + p + 1.0) / 2.0))`です。
  * `["objective"]`: 目的値

# 例

```julia-repl
julia> reg = createRegressionSetting(@formula(calls ~ year), phones);
julia> galts(reg)
Dict{Any,Any} with 3 entries:
  "betas"       => [-56.5219, 1.16488]
  "best.subset" => [3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 23, 24]
  "objective"   => 3.43133
```

# 参考文献

Satman, M. Hakan. "A genetic algorithm based modification on the lts algorithm for large data sets."  Communications in Statistics-Simulation and Computation 41.5 (2012): 644-652.
