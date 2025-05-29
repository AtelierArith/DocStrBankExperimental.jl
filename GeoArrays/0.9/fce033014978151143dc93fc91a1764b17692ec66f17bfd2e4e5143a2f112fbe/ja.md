```
GeoArray(A::AbstractArray{T,2|3} where T <: NumberOrMissing)
```

任意の配列からGeoArrayを構築します。デフォルトの`AffineMap`と`CRS`が生成されます。

# 例

```julia-repl
julia> GeoArray(rand(10,10,1))
10x10x1 Array{Float64, 3} with AffineMap([1.0 0.0; 0.0 1.0], [0.0, 0.0]) and undefined CRS
```
