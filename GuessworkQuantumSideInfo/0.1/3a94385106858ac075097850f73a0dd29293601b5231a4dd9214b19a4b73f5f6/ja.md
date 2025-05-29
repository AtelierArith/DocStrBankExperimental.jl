```
randdm([rng, T = Float64], d)
```

次元 `d` のランダムな密度行列を数値型 `Complex{T}` で生成します。

## 例

```julia
julia> randdm(2)
2×2 Array{Complex{Float64},2}:
 0.477118+0.0im        0.119848-0.0371569im
 0.119848+0.0371569im  0.522882+0.0im      
```
