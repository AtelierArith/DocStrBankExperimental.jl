```
@jenterdata [name][, clauses...]
```

デバイスメモリを割り当てるか、データをデバイスメモリにコピーします。

`name`が指定されていない場合、現在アクティブなアクセルコンテキストが使用されます。

# 引数

  * `name`::String: アクセラレータコンテキストの一意の名前
  * `alloc`::NTuple:
  * `updateto`::NTuple:
  * `async`::Keyword :

他に[`@jaccel`](@jaccel)、[`@jkernel`](@jkernel)を参照してください。

# 例

```julia-repl
julia> @jenterdata myacc alloc(X, Y, Z), updateto(X, Y, Z)
0
```

# 実装

T.B.D. ```
