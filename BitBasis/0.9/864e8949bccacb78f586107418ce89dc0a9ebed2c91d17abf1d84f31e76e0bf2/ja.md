```
neg(index::Integer, nbits::Int) -> Integer
```

全てのビットが反転した整数を返します（ビットの総数は `nbits` です）。

# 例

```jldoctest
julia> neg(0b1111, 4) |> BitStr{4}
0000 ₍₂₎

julia> neg(0b0111, 4) |> BitStr{4}
1000 ₍₂₎
```
