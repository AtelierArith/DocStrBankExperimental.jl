```
scan0(x, n::Integer=1)
scan1(x, n::Integer=1)
```

`x`の中で`n`以降または`n`を含む最初の`0`（`scan0`の場合）または`1`（`scan1`の場合）の位置を返します。

# 例

```jldoctest
julia> scan0(0b10101, 1)
2

julia> scan1(0b10101, 6) == Bits.NOTFOUND
true
```
