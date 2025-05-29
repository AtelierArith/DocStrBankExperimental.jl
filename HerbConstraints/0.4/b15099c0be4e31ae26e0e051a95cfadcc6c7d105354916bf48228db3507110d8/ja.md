```
remove!(solver::GenericSolver, path::Vector{Int}, rule_index::Int)
```

`path`で指定された穴の領域から`rule_index`を削除します。`path`が穴を指していると仮定されており、そうでない場合は例外がスローされます。
