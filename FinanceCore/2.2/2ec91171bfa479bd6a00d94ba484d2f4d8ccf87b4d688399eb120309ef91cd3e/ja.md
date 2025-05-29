```
amount(x)
```

オブジェクトが金額コンポーネントを持っている場合（例：`Cashflow`）、その金額コンポーネントを返します。そうでない場合は単に `x` を返します。

# 例

```julia-repl
julia> FinanceCore.amount(Cashflow(1.,3.))
1.0

julia> FinanceCore.amount(1.)
1.0
```
