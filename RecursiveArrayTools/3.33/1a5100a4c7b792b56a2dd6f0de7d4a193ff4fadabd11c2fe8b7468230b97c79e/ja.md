```julia
recursive_unitless_eltype(a)
```

単位のない要素型を取得します。たとえば、`ones`が`Array{Array{Float64,N},N}`を持っている場合、これは`Array{Float64,N}`を返します。
