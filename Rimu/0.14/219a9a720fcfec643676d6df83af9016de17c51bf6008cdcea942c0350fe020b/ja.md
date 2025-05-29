```
ReportToFile(; kwargs...) <: ReportingStrategy
```

[`ReportingStrategy`](@ref) for [`ProjectorMonteCarloProblem`](@ref) that writes the report directly to a file in the [`Arrow`](https://arrow.apache.org/julia/dev/) format. Useful when dealing with long jobs or large numbers of replicas, when the report can incur a significant memory cost.

The arrow file can be read back in with [`load_df(filename)`](@ref) or `using Arrow; Arrow.Table(filename)`.

# キーワード引数

  * `filename = "out.arrow"`: レポートを出力するファイル。ファイルが既に存在する場合、新しいファイルが作成されます。
  * `reporting_interval = 1`: レポートされるシミュレーションステップ間の間隔。
  * `chunk_size = 1000`: ファイルに書き込まれる各チャンクのサイズ。このサイズの`DataFrame`がメモリに収集され、ディスクに書き込まれます。保存時には、情報メッセージも`io`に印刷されます。
  * `save_if =`[`is_mpi_root()`](@ref Rimu.is_mpi_root): この値がtrueの場合、レポートを保存し、そうでない場合は無視します。
  * `return_df = false`: この値がtrueの場合、ファイルを読み込み、計算の最後にデータフレームを返します。そうでない場合は、空の`DataFrame`が返されます。
  * `io = stdout`: メッセージを印刷するための`IO`。メッセージを表示したくない場合は`devnull`に設定します。
  * `compress = :zstd`: 使用する圧縮アルゴリズム。`:zstd`、`:lz4`、または`nothing`を指定できます。

See also [`load_df`](@ref), [`save_df`](@ref), [`ReportDFAndInfo`](@ref), and [`ProjectorMonteCarloProblem`](@ref).
