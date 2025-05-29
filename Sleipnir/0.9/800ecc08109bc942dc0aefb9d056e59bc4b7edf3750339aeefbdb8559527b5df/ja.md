```
    Parameters(; physical::PhysicalParameters = PhysicalParameters(), simulation::SimulationParameters = SimulationParameters())
```

与えられた物理パラメータとシミュレーションパラメータを使用して `Parameters` オブジェクトを構築します。

# 引数

  * `physical::PhysicalParameters`: `PhysicalParameters` のインスタンス (デフォルト: `PhysicalParameters()`).
  * `simulation::SimulationParameters`: `SimulationParameters` のインスタンス (デフォルト: `SimulationParameters()`).

# 戻り値

  * 提供された物理パラメータとシミュレーションパラメータで初期化された `Parameters` オブジェクト。

# 注意事項

  * `simulation.multiprocessing` が有効になっている場合、指定された数のワーカーでマルチプロセッシングが構成されます。
