```
MetropolisMonteCarlo(; <keyword arguments>)
```

メトロポリスアルゴリズムを使用して構成空間をサンプリングするモンテカルロシミュレーターです。

# 引数

  * `temperature::T`: システムの温度。
  * `trial_moves::M`: 試行移動を実行する関数。
  * `trial_args::Dict`: 試行移動関数に渡される引数の辞書。
