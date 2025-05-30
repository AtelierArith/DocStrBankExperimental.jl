```
approx(f::Function, bbox::Vector{<:Tuple}, c::Curvature, a::Algorithm;  kwargs...)
```

Approximate the function using a uniform sampling over the bounding box `bbox`

Additional keyword arguments:

  * `nsample`: the number of points used in each dimension (default = 10)
