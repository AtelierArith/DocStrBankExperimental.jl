```julia
ApplyBCToSite(site::Vector{Int64}, L::Vector{Int64}, BC::Vector{ComplexF64}) -->  Vector{Int64}
```

与えられた格子サイズ `L` と境界条件 `BC` に基づいて、`site` の有効な実空間オフセットを返します。
