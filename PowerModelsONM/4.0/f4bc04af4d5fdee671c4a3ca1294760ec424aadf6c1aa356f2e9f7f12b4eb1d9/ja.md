```
evaluate_partition_optimality(
    data,
    load_scenarios,
    model_type,
    solver;
    save_partial_results,
    partial_result_folder,
    time_elapsed,
    kwargs...
)
```

特定のパーティションの最適性を評価するための関数で、負荷シナリオのコレクションを考慮します。

`data`には適用されたパーティション構成が含まれています。
