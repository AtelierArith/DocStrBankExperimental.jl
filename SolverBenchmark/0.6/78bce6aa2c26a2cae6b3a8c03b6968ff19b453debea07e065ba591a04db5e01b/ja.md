```
posted_gist = to_gist(results, p)
```

ベンチマーク結果とパフォーマンスプロファイルを含むギストを作成して投稿します。

入力:

  * `results::BenchmarkResults`: `PkgBenchmark.benchmarkpkg`の結果
  * `p`:: `profile_solvers`の結果

出力:

  * GitHub.jlの`create_gist`の戻り値。
