```
has_symbolic_var(eqs, var)
```

式 `eq` にシンボリック変数 `var` が存在する場合は `true` を返し、そうでない場合は `false` を返します。これは `@parameters` または `@variables` のいずれにも対応しています。`var` が `Num` ではなく `Symbol` の場合、すべての変数はその名前に変換され、名前のみを基に等価性がチェックされます。

```
has_symbolic_var(model, var)
```

MTKモデル（例えば `ODESystem`）が与えられた場合、観測変数を含むシステムの*すべての*方程式の中を検索します。
