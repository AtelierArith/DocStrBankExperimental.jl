```
stats = bmark_results_to_dataframes(results)
```

`PkgBenchmark` の結果を `DataFrame` の辞書に変換します。ベンチマーク SUITE は次の形式で構築されている必要があります。

```
SUITE[solver][case] = ...
```

ここで `solver` は DataFrame で比較されるソルバーの一つとして記録され、case はテストケースです。例えば：

```
SUITE["CG"]["BCSSTK09"] = @benchmarkable ...
SUITE["LBFGS"]["ROSENBR"] = @benchmarkable ...
```

入力：

  * `results::BenchmarkResults`: `PkgBenchmark.benchmarkpkg` の結果

出力：

  * `stats::Dict{Symbol,DataFrame}`: ソルバーごとのベンチマーク結果を含む `DataFrame` の辞書。
