```
stats = judgement_results_to_dataframes(judgement)
```

`BenchmarkJudgement` の結果を `DataFrame` の辞書に変換します。

入力:

  * `judgement::BenchmarkJudgement`: 例えば、以下の結果です。

    ```
    commit = benchmarkpkg(mypkg)  # コミットまたはプルリクエストのベンチマーク
    main = benchmarkpkg(mypkg, "main")  # ベースラインベンチマーク
    judgement = judge(commit, main)
    ```

出力:

  * `stats::Dict{Symbol,Dict{Symbol,DataFrame}}`: ターゲットおよびベースラインのベンチマーク結果を含む `Dict{Symbol,DataFrame}` の辞書。 この辞書の要素は、`bmark_results_to_dataframes(main)` および `bmark_results_to_dataframes(commit)` によって返されるものと同じです。
