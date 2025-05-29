```
p = profile_package(judgement)
```

`PkgBenchmark.BenchmarkJudgement` の結果に基づいてパフォーマンスプロファイルを生成します。

入力:

  * `judgement::BenchmarkJudgement`: 例えば、以下の結果です。

    ```
    commit = benchmarkpkg(mypkg)  # コミットまたはプルリクエストのベンチマーク
    main = benchmarkpkg(mypkg, "main")  # ベースラインベンチマーク
    judgement = judge(commit, main)
    ```
