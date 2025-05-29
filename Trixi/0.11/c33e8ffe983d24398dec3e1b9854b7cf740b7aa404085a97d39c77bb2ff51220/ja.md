```
initial_condition_convergence_test(x, t, equations::AcousticPerturbationEquations2D)
```

収束テストに使用される滑らかな初期条件で、[`source_terms_convergence_test`](@ref)と組み合わせて使用されます。`equations`からのグローバル平均値を使用します。
