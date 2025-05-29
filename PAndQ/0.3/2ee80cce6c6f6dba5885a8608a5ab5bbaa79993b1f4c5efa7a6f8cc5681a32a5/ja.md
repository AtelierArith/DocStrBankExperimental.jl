```
value(T = Any, p)
```

もし `p` が定数と論理的に同等であれば、その定数の値を `Some` でラップして返します。そうでなければ、`nothing` を返します。

`Some` でラップされた値は、`something` 関数を使用してアンラップできます。

!!! tip
    コンパイルの遅延を減らすために、定数はラップされた値の型を保存しません。したがって、この値の型は推論できず、ランタイムディスパッチを引き起こす可能性があります。この型がコンパイル時に知られている場合は、最初のパラメータとして渡してください。未型指定の場所から取得した値に関するパフォーマンスのヒントについては、[Annotate values taken from untyped locations](https://docs.julialang.org/en/v1/manual/performance-tips/#Annotate-values-taken-from-untyped-locations)を参照してください。


# 例

```jldoctest
julia> @atomize value(p)

julia> @atomize value($1)
Some(1)

julia> @atomize something(value(Int, $2))
2
```
