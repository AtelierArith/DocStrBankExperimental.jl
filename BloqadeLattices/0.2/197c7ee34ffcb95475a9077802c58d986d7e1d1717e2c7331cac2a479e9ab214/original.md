```
distance(x, y)
distance(region::Parallelepiped{D,T},x,y)
```

Distance between two points. 

If just points `x` and `y` are provided, the Euclidean distance is calculated. 

If a `region` is provided, then it is automatically assumed periodic boundary conditions are enabled and the smallest possible distance between the two points is returned.

```jldoctest; setup=:(using BloqadeLattices)
julia> distance((0.0, 0.0), (1.0, 1.0))
1.4142135623730951

julia> bounds = zeros(2,2); bounds[:,1] .= (3, 0); bounds[:,2] .= (0, 3);

julia> distance(Parallelepiped(bounds), (0.5, 0.5), (2.5, 2.5))
1.4142135623730951
```
