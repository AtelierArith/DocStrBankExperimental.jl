```
bit(x::Integer, i::Integer)       -> typeof(x)
bit(x::AbstractFloat, i::Integer) -> Integer
```

位置 `i` における `x` のビットを返します。値は `0` または `1` です。`x::Integer` の場合、返されるビットは同じ型です。`x::AbstractFloat` がビット型の場合、返されるビットは `x` と同じ [`bitsize`](@ref) の符号付き整数です。詳細は [`tstbit`](@ref) を参照してください。

# 例

```jldoctest
julia> bit(0b101, 1)
0x01

julia> bit(0b101, 2)
0x00

julia> bit(-1.0, 64)
1
```
