```
minkReduce(U, V, W, debug=false)
```

Find the shortest equivalent basis of that lattice formed by {`U`, `V`, `W`}

```jldoctest
julia> U = [1, 2, 3]; V = [-1, 2, 3]; W = [3, 0, 4]; minkReduce(U,V,W)
([-2.0, 0.0, 0.0], [0.0, -2.0, 1.0], [-1.0, 2.0, 3.0])
```
