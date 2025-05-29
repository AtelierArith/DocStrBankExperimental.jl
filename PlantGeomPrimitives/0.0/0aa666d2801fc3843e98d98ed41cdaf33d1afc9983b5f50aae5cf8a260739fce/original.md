```
scale!(m::Mesh, vec::Vec)
```

Scale a mesh `m` along the three axes provided by `vec`.

# Arguments

  * `m`: The mesh to be scaled.
  * `vec`: A vector containing the scaling factors for the x, y, and z axes.

# Examples

```jldoctest
julia> m = Rectangle();

julia> scaling_vector = Vec(2.0, 1.5, 3.0);

julia> scale!(m, scaling_vector);
```
