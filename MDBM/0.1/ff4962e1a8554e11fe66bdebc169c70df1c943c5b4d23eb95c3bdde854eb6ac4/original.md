```
triangulation(DT1::Array{Tuple{Int64,Int64}})::Array{Tuple{Int64,Int64,Int64}}
```

Provide the triangulation (as a list of point-triplets) of the solution point-cloud based on the face-neighbouring n-cubes. DT1 is the result of the edge connection performed by `connect`.
