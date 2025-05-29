```
grad!(q::Edges{Primal},w::Nodes{Primal})
```

Evaluate the discrete gradient of primal nodal data `w` and return it as primal edge data `q`.

# Example

```jldoctest
julia> w = Nodes(Primal,(8,6));

julia> w[3,4] = 1.0;

julia> q = Edges(Primal,(8,6));

julia> grad!(q,w)
Edges{Primal,8,6,Float64} data
u (in grid orientation)
5×8 Array{Float64,2}:
 0.0  0.0  0.0   0.0  0.0  0.0  0.0  0.0
 0.0  0.0  1.0  -1.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0   0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0   0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0   0.0  0.0  0.0  0.0  0.0
v (in grid orientation)
6×7 Array{Float64,2}:
 0.0  0.0   0.0  0.0  0.0  0.0  0.0
 0.0  0.0  -1.0  0.0  0.0  0.0  0.0
 0.0  0.0   1.0  0.0  0.0  0.0  0.0
 0.0  0.0   0.0  0.0  0.0  0.0  0.0
 0.0  0.0   0.0  0.0  0.0  0.0  0.0
 0.0  0.0   0.0  0.0  0.0  0.0  0.0
```
