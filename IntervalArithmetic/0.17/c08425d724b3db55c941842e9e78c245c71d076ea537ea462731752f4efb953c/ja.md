```
signbit(x::Interval)
```

`x`の任意の要素の符号が負である場合は`true`（`1`）を含む区間を返し、`x`の任意の要素が非負である場合は`false`（`0`）を含む区間を返し、`x`が空である場合は空の区間を返します。

# 例

```jldoctest
julia> signbit(@interval(-4))
[1, 1]

julia> signbit(@interval(5))
[0, 0]

julia> signbit(@interval(-4,5))
[0, 1]
```
