```
curl(w::Nodes{Dual}) --> Edges{Primal}
```

Evaluate the discrete curl of `w`. Another way to perform this operation is to construct a `Curl` object and apply it with `*`.

# Example

```jldoctest
julia> C = Curl();

julia> w = Nodes(Dual,(8,6));

julia> w[3,4] = 1.0;

julia> C*w
Edges{Primal,8,6,Float64} data
u (in grid orientation)
5×8 Array{Float64,2}:
 0.0  0.0   0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  -1.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0   1.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0   0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0   0.0  0.0  0.0  0.0  0.0  0.0
v (in grid orientation)
6×7 Array{Float64,2}:
 0.0   0.0  0.0  0.0  0.0  0.0  0.0
 0.0   0.0  0.0  0.0  0.0  0.0  0.0
 0.0  -1.0  1.0  0.0  0.0  0.0  0.0
 0.0   0.0  0.0  0.0  0.0  0.0  0.0
 0.0   0.0  0.0  0.0  0.0  0.0  0.0
 0.0   0.0  0.0  0.0  0.0  0.0  0.0
```
