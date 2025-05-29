```
remove!(solver::UniformSolver, path::Vector{Int}, rules::Vector{Int})
```

`path`で指定された穴の領域からすべての`rules`を削除します。`path`が穴を指していると仮定されており、そうでない場合は例外がスローされます。
