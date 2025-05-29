```
set_default(; kwargs...)
```

latexifyのデフォルトのkwarg値を設定します。

これは`:env`を除くすべてのキーワード引数に対して機能します。これは加算的であり、複数回呼び出すとデフォルトが追加または置き換えられますが、リセットはされません。

例:

```julia
set_default(mult_symbol = "", transpose = true)
```

設定したデフォルトをリセットするには、`reset_default`を使用します。指定したデフォルトを確認するには、`get_default`を使用します。
