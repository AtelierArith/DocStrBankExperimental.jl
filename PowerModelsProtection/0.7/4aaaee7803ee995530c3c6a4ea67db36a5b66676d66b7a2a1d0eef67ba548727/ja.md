```
solve_fault_study(case::Dict{String,Any}, solver; kwargs...)
```

与えられた最適化 `solver` に対して、伝送（matpower）データセットの `case["fault"]` の下にあるすべてのアクティブな故障を使用して故障研究を解決します。

`kwargs` は、PowerModels の run_model 関数の有効なキーワード引数である可能性があります。
