```
grid_search(f, grid::AbstractGrid; save_vals=Val(false), minimise=Val(false), parallel=Val(false))
```

与えられた `grid` と関数 `f` に対して、グリッドサーチを実行します。

# 引数

  * `f`: 最適化する関数。
  * `grid::AbstractGrid`: 最適化に使用するグリッド。

# キーワード引数

  * `save_vals=Val(false)`: 関数の値を含む配列を返すかどうか。
  * `minimise=Val(false)`: 関数を最小化するか最大化するか。
  * `parallel=Val(false)`: マルチスレッドでグリッドサーチを実行するかどうか。
