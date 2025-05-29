```
get_triangle(m::Mesh, i)
```

Retrieve the vertices for the i-th triangle in a mesh.

# Arguments

  * `mesh`: The mesh from which to retrieve the triangle.
  * `i`: The index of the triangle to retrieve.

# Returns

A vector containing the three vertices defining the i-th triangle.

# Example

```jldoctest
julia> v = [Vec(0.0, 0.0, 0.0), Vec(0.0, 1.0, 0.0), Vec(1.0, 0.0, 0.0),
            Vec(0.0, 0.0, 0.0), Vec(0.0, 1.0, 0.0), Vec(0.0, 0.0, 1.0)];

julia> m = Mesh(v);

julia> get_triangle(m, 2);
```
