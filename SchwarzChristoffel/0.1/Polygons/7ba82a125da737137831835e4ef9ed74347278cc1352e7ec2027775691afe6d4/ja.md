```
interiorangle(p::Polygon) -> Vector{Float64}
```

多角形 `p` の内部角度（$\pi$ で割ったもの）のベクトルを返します。

# 例

```jldoctest
julia> p = Polygon([-1.0,0.2,1.0,-1.0],[-1.0,-1.0,0.5,1.0]);

julia> interiorangle(p)
4-element Array{Float64,1}:
 0.5
 0.655958
 0.422021
 0.422021
```
