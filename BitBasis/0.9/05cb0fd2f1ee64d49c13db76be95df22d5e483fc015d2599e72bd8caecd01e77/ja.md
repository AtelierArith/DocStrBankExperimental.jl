```
flip(index::Integer, mask::Integer) -> Integer
```

マスクされた位置のビットを反転させた整数を返します。

# 例

```jldoctest
julia> flip(0b1011, 0b1011) |> BitStr{4}
0000 ₍₂₎
```
