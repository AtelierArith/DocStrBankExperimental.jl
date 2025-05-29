```
ConvergenceChecker(;
    norm_condition,
    component_condition,
    condition_combiner,
    norm = LinearAlgebra.norm,
)
```

シーケンス `val[0], val[1], val[2], ...` がある限界 `L` に収束したかどうかを確認します。これは、エラー `err[iter] = val[iter] .- L` を考慮して行われます。これは `is_converged!(::ConvergenceChecker, cache, val, err, iter)` を呼び出すことで行われ、ここで `val = val[iter]` および `err = err[iter]` です。`L` の値が不明な場合、`err` は `err[iter]` の近似値である可能性があります。`ConvergenceChecker` の `cache` は `allocate_cache(::ConvergenceChecker, val_prototype)` を使用して取得でき、ここで `val_prototype` は `val` および `err` に似ています。

`ConvergenceChecker` は2種類のチェックを行うことができます。すなわち、`norm(val)` と `norm(err)` がいくつかの `ConvergenceCondition` を満たすかどうかを確認すること、そして `abs.(val)` と `abs.(err)` のすべてのコンポーネントが個別にいくつかの `ConvergenceCondition` を満たすかどうかを確認することです。これら2つのチェックは、`&` または `|` で組み合わせることができます。いずれかのチェックが不要な場合、対応する `ConvergenceCondition` を `nothing` に設定できます。

`LinearAlgebra.norm` の代わりに、`norm` は `val` と `err` を非負のスカラー値に変換する任意のものに設定できます。
