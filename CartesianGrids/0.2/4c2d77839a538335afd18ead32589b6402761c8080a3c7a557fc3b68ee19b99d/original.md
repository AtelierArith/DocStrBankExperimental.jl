```
product(p::Edges/Nodes,q::Edges/Nodes) --> Edges/Nodes
```

Compute the Hadamard product of edge or nodal (primal or dual) data `p` and `q` and return the result. This operation can also be carried out with the `∘` operator:

# Example

```jldoctest
julia> q = Edges(Dual,(8,6));

julia> p = deepcopy(q);

julia> q.u[3,2] = 0.3;

julia> p.u[3,2] = 0.2;

julia> p∘q
Edges{Dual,8,6,Float64} data
u (in grid orientation)
6×7 Array{Float64,2}:
 0.0  0.0  0.0   0.0  0.0  0.0  0.0
 0.0  0.0  0.0   0.0  0.0  0.0  0.0
 0.0  0.0  0.0   0.0  0.0  0.0  0.0
 0.0  0.0  0.0   0.0  0.0  0.0  0.0
 0.0  0.0  0.06  0.0  0.0  0.0  0.0
 0.0  0.0  0.0   0.0  0.0  0.0  0.0
v (in grid orientation)
5×8 Array{Float64,2}:
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
```
