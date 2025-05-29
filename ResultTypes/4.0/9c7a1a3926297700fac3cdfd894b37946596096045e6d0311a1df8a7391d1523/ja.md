```
unwrap(result::Result{T, E}) -> T
unwrap(val::T) -> T
unwrap(::Type{T}, result_or_val) -> T
```

`result`が型`T`の値を保持していると仮定し、それを返します。もし`result`が例外を保持している場合、その例外がスローされます。

`unwrap`の引数が`Result`でない場合、それが返されます。

2つの引数を持つ`unwrap`の形式は、2番目の引数に対して`unwrap`を呼び出し、その後それを型`T`に変換します。
