```
posted_gist = to_gist(results)
```

ベンチマーク結果とパフォーマンスプロファイルを含むギストを作成して投稿します。

入力:

  * `results::BenchmarkResults`: `PkgBenchmark.benchmarkpkg`の結果

出力:

  * GitHub.jlの`create_gist`の戻り値。
