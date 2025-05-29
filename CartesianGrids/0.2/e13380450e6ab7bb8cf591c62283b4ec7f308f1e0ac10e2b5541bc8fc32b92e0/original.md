```
divergence(q::Edges) --> Nodes
```

Evaluate the discrete divergence of edge data `q`. Can also perform this operation by creating an object of Divergence type and applying it with `*`.

# Example

```jldoctest
julia> D = Divergence();

julia> q = Edges(Primal,(8,6));

julia> q.u[3,2] = 1.0;

julia> D*q
Nodes{Primal,8,6,Float64} data
Printing in grid orientation (lower left is (1,1))
5×7 Array{Float64,2}:
 0.0  0.0   0.0  0.0  0.0  0.0  0.0
 0.0  0.0   0.0  0.0  0.0  0.0  0.0
 0.0  0.0   0.0  0.0  0.0  0.0  0.0
 0.0  1.0  -1.0  0.0  0.0  0.0  0.0
 0.0  0.0   0.0  0.0  0.0  0.0  0.0
```
