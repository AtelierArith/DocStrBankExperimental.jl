```
@unpack_option [should_throw=false] options unpack_expr
```

`options` から `unpack_expr` の形式に応じて値を展開します。

`unpack_expr` が `name` の形式で、`name::Symbol` の場合、このマクロは次のように書くことと同等です。

```julia
$name = options[$name]
```

`should_throw == true` の場合、`options` にキー `$name` が含まれていないと `ArgumentError` をスローします。

そうでない場合、`options` にキー `$name` が含まれていないと現在の関数から `ArgumentError` を返します。

`unpack_expr` が次の形式の場合：

  * `name::T` の場合、`options[$name]` は型 `T` でなければならず、そうでない場合は `ArgumentError` が *返されます*
  * `name::Union{T1, T2, ..., Tn}` の場合、`options[$name]` は型 `T1, T2, ...,` または `Tn` でなければなりません
  * `name = default` の場合、`$name` が `options` に存在しないときは `default_value` が使用されます
  * `name => new_name` の場合、`$new_name = options[$name]` と同等です

`(name => new_name)::T`、`name::T = default` または `name::Union{T1, T2, ..., Tn} = default` の形式の `unpack_expr` も期待通りに動作します。
