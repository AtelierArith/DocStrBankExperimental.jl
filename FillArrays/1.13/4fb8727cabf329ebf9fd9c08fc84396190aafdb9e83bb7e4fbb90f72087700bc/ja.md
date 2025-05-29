```
Fill{T, N, Axes} where {T,N,Axes<:Tuple{Vararg{AbstractUnitRange,N}}}
```

定数の型 `T` に等しいすべてのエントリを持つ次元 `N` の配列の遅延表現で、型 `Axes` の軸を持ちます。通常、`Fill` や `Zeros` または `Ones` によって作成されます。

# 例

```jldoctest
julia> Fill(7, (2,3))
2×3 Fill{Int64}, with entries equal to 7

julia> Fill{Float64, 1, Tuple{UnitRange{Int64}}}(7.0, (1:2,))
2-element Fill{Float64, 1, Tuple{UnitRange{Int64}}} with indices 1:2, with entries equal to 7.0
```
