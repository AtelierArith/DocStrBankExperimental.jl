```
nvariables(expr::Expression; parameters = Variable[])
nvariables(exprs::AbstractVector{Expression}; parameters = Variable[])
```

与えられた式で使用されている変数の数を取得しますが、`parameters`で宣言された変数はカウントしません。
