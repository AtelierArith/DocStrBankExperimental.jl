```
@jexitdata [name][, clauses...]
```

デバイスメモリの解放またはデバイスメモリからのデータのコピーを行います。

`name`が指定されていない場合、現在アクティブなアクセラレータコンテキストが使用されます。

# 引数

  * `name`::String: アクセラレータコンテキストの一意の名前
  * `delete`::NTuple:
  * `updatefrom`::NTuple:
  * `async`::Keyword :

関連項目 [`@jaccel`](@jaccel), [`@jkernel`](@jkernel)

# 例

```julia-repl
julia> @jexitdata myacc delete(X, Y, Z), updatefrom(X, Y, Z)
0
```

# 実装

T.B.D.
