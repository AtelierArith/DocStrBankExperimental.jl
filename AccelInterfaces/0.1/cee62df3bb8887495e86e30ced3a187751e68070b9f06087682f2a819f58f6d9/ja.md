```
@jdecel [name][, clauses...]
```

アクセラレータコンテキストを破棄します。

`name`が指定されていない場合、このコンテキストには現在アクティブなコンテキストとしてのみアクセスできます。

# 引数

  * `name`::String: このアクセラレータコンテキストの一意の名前

関連項目としては [`@jaccel`](@jaccel)、[`@jkernel`](@jkernel) があります。

# 例

```julia-repl
julia> @jdecel myacc
```

# 実装

T.B.D. ```
