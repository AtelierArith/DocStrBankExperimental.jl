```
AdditionProcess(process, added...)
```

与えられた `process` の `rhs` にプロセス `added` を追加するための便利なプロセスです。`added` は単一のシンボリック表現であることができます。それ以外の場合、`added` は `Process` または `Equation`、またはそれらの多数であることができ、その場合、すべての追加コンポーネントにわたって `lhs_variable` が `process` と一致することが確認されます。
