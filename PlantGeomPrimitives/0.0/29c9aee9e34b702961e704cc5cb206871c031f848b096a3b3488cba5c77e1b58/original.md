```
Mesh(meshes)
```

Merge multiple meshes into a single one

# Arguments

  * `meshes`: Vector of meshes to merge.

# Returns

A new `Mesh` object that is the result of merging all the input meshes.

# Example

```jldoctest
julia> e = Ellipse(length = 2.0, width = 2.0, n = 10);

julia> r = Rectangle(length = 10.0, width = 0.2);

julia> m = Mesh([e,r]);
```
