```
findmax(f, domain) -> (f(x), index)
```

コドメインの値（`f`の出力）と、対応する値のインデックス（`f`の入力）からなるペアを返します。`f(x)`が最大化されるようにします。最大点が複数ある場合は、最初のものが返されます。

`domain`は空でないイテラブルでなければなりません。

値は`isless`で比較されます。

!!! compat "Julia 1.7"
    このメソッドはJulia 1.7以降が必要です。


# 例

```jldoctest
julia> findmax(identity, 5:9)
(9, 5)

julia> findmax(-, 1:10)
(-1, 1)

julia> findmax(first, [(1, :a), (3, :b), (3, :c)])
(3, 2)

julia> findmax(cos, 0:π/2:2π)
(1.0, 1)
```
