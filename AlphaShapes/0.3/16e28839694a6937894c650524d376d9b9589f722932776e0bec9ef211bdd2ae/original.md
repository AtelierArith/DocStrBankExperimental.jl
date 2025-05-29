```
AlphaShape(X::AbstractArray{Float64,2};α::Union{Nothing,Float64}=nothing,
    search::Tuple{Float64,Float64}=(0.0, 10.0),
    MaxSteps::Int=100)::AbstractArray{Float64,3}
```

Find the alpha shape corresponding to the 2D AbstractArray of points X: [2,npoints], and the α value α.

If α == nothing then a search over the range of values search is done to find the best value. The optimisation objective is the alpha shape area (minimise) subject to all points in X being included in the alpha shape triangulation.
