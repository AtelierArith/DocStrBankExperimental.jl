```
copysign(x, y) -> z
```

`z`は`x`の大きさを持ち、`y`と同じ符号を持ちます。

# 例

```jldoctest
julia> copysign(1, -2)
-1

julia> copysign(-1, 2)
1
```
