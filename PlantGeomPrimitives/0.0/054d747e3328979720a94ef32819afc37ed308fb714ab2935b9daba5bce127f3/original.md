```
translate!(m::Mesh, v::Vec)
```

Translate the mesh `m` by vector `v`.

# Arguments

  * `m`: The mesh to be translated.
  * `v`: The vector by which the mesh is to be translated.

# Examples

```jldoctest
julia> m = Rectangle();

julia> v = Vec(2.0, 1.5, 3.0);

julia> translate!(m, v);
```
