```
FuncArg(; name, type, value::Any, is_splat::Bool)
```

関数引数式に一致します

# フィールド

  * `name::Union{NotProvided, Symbol} = not_provided`: 引数の名前
  * `type::Union{NotProvided, Symbol, Expr} = not_provided`: 引数の注釈付き型。`value`が提供されていない場合のみ有効です。
  * `value::Any = not_provided`: 引数の値。`name`が提供されている場合、これはメソッド定義における`name`のデフォルト値に対応します。そうでない場合、これは関数引数として渡される値です。
  * `is_splat::Bool = false`: この引数がスプラットされている場合は`true`、そうでない場合は`false`です。
