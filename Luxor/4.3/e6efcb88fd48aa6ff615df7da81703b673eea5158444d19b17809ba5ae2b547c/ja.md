```
polysidelengths(p::Vector{Point}; closed = true)
```

多角形 `p` の各「辺」の長さを含む配列を返します。

`closed = false` の場合、最後の点から最初の点への辺は含まれません。

```julia
polysidelengths(ngon(O, 100, 4))
4-element Vector{Float64}:
 141.42135623730948
 141.4213562373095
 141.4213562373095
 141.42135623730954

polysidelengths(ngon(O, 100, 4), closed=false)
3-element Vector{Float64}:
 141.42135623730948
 141.4213562373095
 141.4213562373095
```
