```
grad(w::Nodes{Primal}) --> Edges{Primal}
```

Evaluate the discrete gradient of primal nodal data `w`. Can also perform this operation by creating an object of Grad type and applying it with `*`.

# Example

```jldoctest
julia> w = Nodes(Primal,(8,6));

julia> w[3,4] = 1.0;

julia> G = Grad();

julia> G*w
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
