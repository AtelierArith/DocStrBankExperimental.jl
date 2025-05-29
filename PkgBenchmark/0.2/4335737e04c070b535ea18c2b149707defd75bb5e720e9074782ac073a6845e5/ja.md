```
export_markdown(file::String, results::BenchmarkResults)
export_markdown(io::IO,       results::BenchmarkResults)
export_markdown(file::String, results::BenchmarkJudgement; export_invariants=false)
export_markdown(io::IO,       results::BenchmarkJudgement; export_invariants=false)
```

`results`を`file`または`io`にマークダウン形式で書き込みます。

`BenchmarkJudgement`をエクスポートする際、デフォルトでは可能な回帰または改善に対応する結果のみが含まれます。不変の結果もエクスポートするには、`export_invariants=true`を設定します。

参照: [`BenchmarkResults`](@ref), [`BenchmarkJudgement`](@ref)
