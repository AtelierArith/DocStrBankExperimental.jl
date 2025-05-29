```
from_expr(::Type{T}, expr; throw_error::Bool=false, kwargs...)
```

`expr`を型`T`のオブジェクトにパースします。

提供された`kwargs`は、基盤となるパース関数に渡されます。

もし`expr`が型`T`のオブジェクトにパースできない場合 - `throw_error == true`の場合は`ArgumentError`をスローします - それ以外の場合は`nothing`を返します。

====================

```
from_expr(::Type{Vector{T}}, expr::Expr; throw_error::Bool=false)
```

`tuple`または`vect`の`expr`を`Vector{T}`としてパースします。`expr`の各引数は型`T`でなければなりません。

====================

```
from_expr(::Type{Vector{T}}, input::T; throw_error::Bool=false)
```

`input`を含む単一の`Vector{T}`を返します。

====================

```
from_expr(::Type{FuncCall}, expr; normalize_kwargs::Bool=false)
```

`expr`からパースされた`FuncCall`を返します。

`normalize_kwargs = true`の場合、末尾の等式式（例：`f(a, b, c=1)`）はキーワード引数としてパースされます。
