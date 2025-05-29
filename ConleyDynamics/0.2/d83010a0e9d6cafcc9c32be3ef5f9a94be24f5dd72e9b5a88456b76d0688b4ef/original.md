```
create_spatial_mvf(lc::LefschetzComplex, coords::Vector{Vector{Float64}}, vf)
```

Create a spatial multivector field from a regular vector field.

The function expects a three-dimensional Lefschetz complex `lc` and a coordinate vector `coords` of coordinates for all the 0-dimensional cells in the complex. Moreover, the underlying vector field is specified by the function `vf(z::Vector{Float64})::Vector{Float64}`, where both the input and output vectors have length three. The function `create_spatial_mvf` returns a multivector field `mvf` on `lc`, which can then be further analyzed using for example the function `connection_matrix`.

The input data `lc` and `coords` has to be of one of the following two types:

  * `lc` is a tetrahedral mesh of a region in three dimensions. In other words, the underlying Lefschetz complex is in fact a simplicial  complex, and the vector `coords` contains the vertex coordinates.
  * `lc` is a three-dimensional cubical complex, i.e., it is the closure of a collection of three-dimensional cubes in space. The vertex coordinates can be slightly perturbed from the original position in the cubical lattice, as long as the overall structure  of the complex stays intact. In that case, the faces are interpreted as Bezier surfaces with straight edges.

# Example 1

Suppose we define a sample vector field using the commands

```julia
function samplevf(x::Vector{Float64})
    #
    # Sample vector field with nontrivial Morse decomposition
    #
    x1, x2, x3 = x
    y1 = x1 * (1.0 - x1*x1)
    y2 = -x2
    y3 = -x3
    return [y1, y2, y3]
end
```

One first creates a cubical complex covering the interesting dynamics, say the trapping region `[-1.5,1.5] x [-1,1] x [-1,1]`, using the commands

```julia
lc, coords = create_cubical_box(3,3,3);
coordsN = convert_spatial_coordinates(coords,[-1.5,-1.0,-1.0],[1.5,1.0,1.0]);
```

The multivector field is then generated using

```julia
mvf = create_spatial_mvf(lc,coordsN,samplevf);
```

and the commands

```julia
cm = connection_matrix(lc, mvf);
cm.conley
full_from_sparse(cm.matrix)
```

finally show that this vector field gives rise to a Morse decomposition with three Morse sets, and two connecting orbits.
