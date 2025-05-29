```
unwrap_error(result::Result{T, E}) -> E
unwrap_error(exception::E) -> E
```

`result`が型`E`の例外を保持していると仮定し、それを返します。もし`result`が値を保持している場合は、例外をスローします。

`unwrap_error`の引数が`Exception`である場合、その例外が返されます。
