```
(launcher::Launcher)(arch::Architecture, grid, kernel_and_args::Pair{F,Args}; bc=nothing) where {F,Args}
```

指定された `arch`、`grid`、`kernel_and_args`、およびオプションの境界条件（`bc`）を使用して計算カーネルを起動します。

## 引数:

  * `arch::Architecture`: 計算を実行するアーキテクチャ。
  * `grid`: 計算領域を定義するグリッド。
  * `kernel_and_args::Pair{F,Args}`: 計算カーネル `F` とその引数 `Args` からなるペア。
  * `bc=nothing`: 計算のためのオプションの境界条件。

!!! 警告       * `arch` は `Launcher` のアーキテクチャと互換性がある必要があります。       * `bc` が `nothing` の場合、カーネルは境界条件なしで起動されます。       * 関数は計算が完了するまで待機してから戻ります。
