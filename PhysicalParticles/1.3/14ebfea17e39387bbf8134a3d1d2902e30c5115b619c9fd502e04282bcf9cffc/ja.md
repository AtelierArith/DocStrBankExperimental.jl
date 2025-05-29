```
pconvert(a::Abstractay{T,2}) where T<:Number
```

2xN 配列を Array{PVector2D,1} に、3xN 配列を Array{PVector,1} に変換します。

## 例

```jl
julia> pconvert([1.0 3.0; 
                 2.0 4.0])
2-element Vector{PVector2D}:
 PVector2D{Float64}(1.0, 2.0)
 PVector2D{Float64}(3.0, 4.0)

julia> pconvert([1.0 4.0;
                 2.0 5.0;
                 3.0 6.0])
2-element Vector{PVector}:
 PVector{Float64}(1.0, 2.0, 3.0)
 PVector{Float64}(4.0, 5.0, 6.0)
```
