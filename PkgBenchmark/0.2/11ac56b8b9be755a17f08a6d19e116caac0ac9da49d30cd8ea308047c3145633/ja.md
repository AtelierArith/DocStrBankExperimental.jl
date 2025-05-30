パッケージのベンチマークを実行した結果を保存します。

以下の（エクスポートされていない）メソッドは `BenchmarkResults`（以下 `results` として記述）に定義されています：

  * `name(results)::String` - ベンチマークされたパッケージのコミット
  * `commit(results)::String` - ベンチマークされたパッケージのコミット。パッケージリポジトリが汚れている場合、文字列 `"dirty"` が返されます。
  * `juliacommit(results)::String` - ベンチマークを実行したJulia実行可能ファイルのコミット
  * `benchmarkgroup(results)::BenchmarkGroup` - ベンチマークの結果を含む [`BenchmarkGroup`](https://github.com/JuliaCI/BenchmarkTools.jl/blob/master/doc/manual.md#the-benchmarkgroup-type)
  * `date(results)::DateTime` - ベンチマークが実行された時間
  * `benchmarkconfig(results)::BenchmarkConfig` - ベンチマークに使用された [`BenchmarkConfig`](@ref)

`BenchmarkResults` は関数 [`export_markdown`](@ref) を使用してマークダウンにエクスポートできます。
