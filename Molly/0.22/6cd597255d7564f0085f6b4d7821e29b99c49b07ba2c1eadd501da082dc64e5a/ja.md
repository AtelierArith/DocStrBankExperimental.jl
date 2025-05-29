```
simulate!(system, simulator, n_steps; <keyword arguments>)
simulate!(system, simulator; <keyword arguments>)
```

シミュレーターのルールに従ってシステムのシミュレーションを実行します。

カスタムシミュレーターはこの関数を実装する必要があります。

# 引数

  * `n_threads=Threads.nthreads()`: シミュレーションを実行するスレッドの数。CPU上で実行する場合にのみ関連します。
  * `run_loggers`: シミュレーション中にロガーを実行するかどうか。`true`、`false`、または`：skipzero`のいずれかで、`run_loggers`が`true`の場合は最初のステップの前にロガーは実行されません。`run_loggers`はデフォルトで`true`ですが、[`SteepestDescentMinimizer`](@ref)の場合は`false`です。
  * `rng=Random.default_rng()`: シミュレーションに使用される乱数生成器。この設定により、再現可能な確率的シミュレーションが可能になります。
