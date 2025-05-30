```
policy, si = solve_info(solver, problem)
```

ソルバーによって決定されたポリシーと、そのポリシーの計算からの情報（通常は `NamedTuple`、`Dict` または `nothing`）を含むタプルを返します。

デフォルトでは、情報として `nothing` を返します。
