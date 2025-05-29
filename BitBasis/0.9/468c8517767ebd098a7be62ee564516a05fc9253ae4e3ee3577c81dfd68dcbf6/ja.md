```
swapbits(n::Integer, mask_ij::Integer) -> Integer
swapbits(n::Integer, i::Int, j::Int) -> Integer
```

`i` と `j` のビットが反転された整数を返します。

# 例

```jldoctest
julia> swapbits(0b1011, 0b1100) == 0b0111
true
```

!!! tip
    マスクで指定された位置 `i` と `j` は、[`bmask`](@ref) が単純でないが定数で知られている場合に、より高速になる可能性があります。


!!! warning
    `mask_ij` は2つの `1` のみを含むべきであり、`swapbits` はそれをチェックしません。自己責任で使用してください。

