```
low0(x, n::Integer=1)
low1(x, n::Integer=1)
```

`x`の`n`番目の`0`（`low0`の場合）または`1`（`low1`の場合）の位置を返します。

# 例

```jldoctest
julia> low0(0b10101, 2)
4

julia> low1(0b10101, 4) == Bits.NOTFOUND
true
```
