```
LocalUnique <: AbstractLocalConstraint
```

与えられた `rule` が指定された `path` で最大1回出現することを強制します。UniformSolverの場合、新しい穴が出現することはないため、`holes` のリストをキャッシュします。
