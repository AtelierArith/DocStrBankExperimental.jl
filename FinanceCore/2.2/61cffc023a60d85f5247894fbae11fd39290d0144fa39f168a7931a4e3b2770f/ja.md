```
timepoint(x,t)
```

`x`が定義された時間コンポーネントを持つオブジェクト（例：`Cashflow`）であれば、その時間コンポーネントを返し、そうでなければ`t`を返します。これは、`Cashflow`または別々の金額と時間ベクトルを処理したい場合に便利です。

# 例

```julia-repl
julia> FinanceCore.timepoint(Cashflow(1.,3.),"ignored")
3.0

julia> FinanceCore.timepoint(1.,4.)
4.0
```
