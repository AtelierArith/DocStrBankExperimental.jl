```julia
GetBCPhase(site::Vector{Int64}, L::Vector{Int64}, BC::Vector{ComplexF64}) --> ComplexF64
```

与えられた格子サイズ `L` と境界条件 `BC` に対して、`site` の有効な位相を返します。
