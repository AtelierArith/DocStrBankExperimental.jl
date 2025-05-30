```
interiornodes(x̄, bc)
```

Returns an interior grid corresponding to the boundary condition `bc` given extended grid `x̄`.

```jldoctest; setup = :(using SimpleDifferentialOperators)
julia> x̄ = 0:5
0:5

julia> interiornodes(x̄, (Reflecting(), Reflecting()))
1:4

julia> x̄ = [1.0; 1.5; 1.7]
3-element Array{Float64,1}:
 1.0
 1.5
 1.7

julia> interiornodes(x̄, (Mixed(1.0), Mixed(1.0)))
1-element Array{Float64,1}:
 1.5
```
