```
cross3!(
    result::AbstractVector{T1},
    theta::Union{AbstractVector{T2}, Tuple{T2, T2, T2}},
    v::Union{AbstractVector{T3}, Tuple{T3, T3, T3}}
) where {T1, T2, T3}
```

三次元空間における二つのベクトルの外積をインプレースで計算します。
