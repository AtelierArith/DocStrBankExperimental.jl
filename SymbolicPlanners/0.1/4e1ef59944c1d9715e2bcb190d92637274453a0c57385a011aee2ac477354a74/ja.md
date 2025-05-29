```
MultiSolution(solutions::Solution...)
MultiSolution(solutions::Tuple, [selector])
```

複数の [`Solution`](@ref) の組み合わせであり、`selector` 関数 `(solutions, [state]) -> sol` に従って選択されます。この関数は使用する解を返します（現在の `state` に依存する場合があります）。`selector` は常に最初の解を返すようにデフォルト設定されています。
