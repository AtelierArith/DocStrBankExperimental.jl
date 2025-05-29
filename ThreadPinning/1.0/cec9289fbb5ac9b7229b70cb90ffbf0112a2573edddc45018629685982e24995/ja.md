```
threadinfo(;
    groupby = :sockets,
    threadpool = :default,
    blas = false,
    slurm = false,
    hints = false,
    compact = true,
    hyperthreads = SysInfo.hyperthreading_is_enabled(),
    efficiency = SysInfo.ncorekinds() > 1,
    masks = false,
    coregaps = SysInfo.hyperthreading_is_enabled(),
    logical = false,
    color = true,
    blocksize = choose_blocksize()
)
```

Juliaスレッドに関する情報を表示します。例えば、どのCPUスレッド（ハイパースレッディングが無効な場合はコア）で実行されているかを示します。

# キーワード引数

  * `groupby`: オプションは `:sockets`、`:numa`、`:cores`、または `:none` です。
  * `threadpool`: 指定されたスレッドプール内のJuliaスレッドのみを考慮します。サポートされている値は `:default`、`:interactive`、および `:all` です。
  * `blas`: Juliaスレッドの代わりにBLASスレッドを視覚化します。
  * `slurm`: アクティブなSLURM割り当てによってカバーされているシステムの部分のみを表示します。
  * `hints`: スレッド関連の設定を改善するためのヒントを提供しようとします。
  * `compact`: コンパクトな順序と「ハイパースレッドの前にコア」の順序を切り替えます。
  * `hyperthreads`: `true`の場合、CPUコア内の最初のスレッドでないCPUスレッドを強調表示しようとします。
  * `efficiency`: `true`の場合、効率コアに属するCPUスレッドを強調表示（下線）します。
  * `masks`: すべてのJuliaスレッドのアフィニティマスクを表示します。
  * `coregaps`: 印刷時に異なるCPUコアの間に追加のスペース（「ギャップ」）を入れます。
  * `logical`: 論理CPUスレッドインデックスと「物理」CPUスレッドインデックスを切り替えます。
  * `color`: カラー出力と白黒出力を切り替えます。
  * `blocksize`: `blocksize`の数だけCPUスレッドの後で新しい行に折り返します。`numa`に設定することもでき、その場合は各NUMAドメインの後で改行が発生します。
