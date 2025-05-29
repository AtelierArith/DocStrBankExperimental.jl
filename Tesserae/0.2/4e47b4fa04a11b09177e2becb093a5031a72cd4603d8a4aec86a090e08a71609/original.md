```
MPValue([T,] interpolation, mesh)
```

`MPValue` stores properties for interpolation, such as the basis function values and its derivatives.

```jldoctest
julia> mesh = CartesianMesh(1.0, (0,5), (0,5));

julia> xₚ = Vec(2.2, 3.4); # particle position

julia> mp = MPValue(BSpline(Quadratic()), mesh);

julia> update!(mp, xₚ, mesh) # update `mp` at position `xₚ` in `mesh`
MPValue:
  Interpolation: BSpline(Quadratic())
  Property names: w::Matrix{Float64}, ∇w::Matrix{Vec{2, Float64}}
  Neighboring nodes: CartesianIndices((2:4, 3:5))

julia> sum(mp.w) ≈ 1 # partition of unity
true

julia> nodeindices = neighboringnodes(mp) # grid indices within a particles' local domain
CartesianIndices((2:4, 3:5))

julia> sum(eachindex(nodeindices)) do ip # linear field reproduction
           i = nodeindices[ip]
           mp.w[ip] * mesh[i]
       end ≈ xₚ
true
```
