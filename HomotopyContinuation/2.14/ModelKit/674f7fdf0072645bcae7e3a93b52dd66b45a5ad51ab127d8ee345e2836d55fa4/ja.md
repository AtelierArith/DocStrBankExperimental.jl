```
degree(f::Expression, vars = variables(f); expanded = false)
```

式 `f` の `vars` における次数を計算します。`expanded` が `true` でない限り、式は最初に展開されます。
