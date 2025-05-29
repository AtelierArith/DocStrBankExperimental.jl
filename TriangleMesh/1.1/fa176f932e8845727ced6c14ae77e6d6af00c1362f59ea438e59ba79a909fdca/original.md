```
polygon_struct_from_points(point :: Array{Float64,2},
                                pm :: Array{Int,2},
                                pa :: Array{Float64,2})
```

Create a polygon from a set of points (example code). No segments or holes are set here.

# Arguments

  * `point :: Array{Float64,2}`: point set (dimension n-by-2)
  * `pm :: Array{Int,2}`: each point can have a marker (dimension either n-by-0 or n-by-1)
  * `pa :: Array{Float64,2}`: each point can have a number of $k>=0$real attributes (dimension n-by-k)
