```
breflect(b::Integer[, masks::Vector{Integer}]; nbits) -> Integer
```

左から右に反射された整数を返します。

# 例

ビットの順序を反射します。

```jldoctest
julia> breflect(0b1011; nbits=4) == 0b1101
true
```
