```
uniquelats(A::ClimArray) → idxs, lats
uniquelats(c::Vector{<:AbstractVector}) → idxs, lats
```

`A`のユニークな緯度を見つけます。`lats`の各緯度がカバーするインデックス（範囲のベクトル）と、緯度自体を返します。
