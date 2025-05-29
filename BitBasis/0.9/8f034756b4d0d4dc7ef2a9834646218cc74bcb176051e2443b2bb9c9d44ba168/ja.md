```
setbit(index::Integer, mask::Integer) -> Integer
```

マスクされた位置のビットを1に設定します。

# 例

```jldoctest
julia> setbit(0b1011, 0b1100) |> BitStr{4}
1111 ₍₂₎

julia> setbit(0b1011, 0b0100) |> BitStr{4}
1111 ₍₂₎

julia> setbit(0b1011, 0b0000) |> BitStr{4}
1011 ₍₂₎
```
