```
@unwrap_error_or(expr, exec)
```

`expr`を`Result`として評価します。もし`expr`が結果値であれば、`exec`を評価してそれを返します。そうでなければ、`expr`のラップされたエラー値を返します。

参照: [`@unwrap_or`](@ref) ```
