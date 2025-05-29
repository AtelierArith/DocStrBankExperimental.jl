```
distinct_certified_solutions(F, S, p = nothing; threading::Bool = true, show_progress::Bool = true, certify_solution_kwargs...)
```

`DistinctCertifiedSolutions` 構造体を返し、システム `F` の解のベクトル `S` から得られた異なる認証済み解を含みます。`certify` と比較して、これはすべての証明書ではなく、異なる認証済み解のみを保持します。これは特に、複数の大きな解のセットを一つの異なる認証済み解のセットに統合したい場合に便利です。
