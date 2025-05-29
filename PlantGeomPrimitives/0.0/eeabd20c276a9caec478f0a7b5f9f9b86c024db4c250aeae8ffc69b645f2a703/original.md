```
BBox(m::Mesh)
```

Build a tight axis-aligned bounding box around a `Mesh` object.

# Arguments

  * `m`: The mesh to build the bounding box around.

# Examples

```jldoctest
julia> m = Rectangle();

julia> box = BBox(m);
```
