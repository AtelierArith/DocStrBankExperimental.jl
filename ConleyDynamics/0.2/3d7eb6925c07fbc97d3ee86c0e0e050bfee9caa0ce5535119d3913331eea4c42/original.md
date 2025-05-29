```
create_planar_mvf(lc::LefschetzComplex, coords::Vector{Vector{Float64}}, vf)
```

Create a planar multivector field from a regular vector field.

The function expects a planar Lefschetz complex `lc` and a coordinate vector `coords` of coordinates for all the 0-dimensional cells in the complex. Moreover, the underlying vector field is specified by the function `vf(z::Vector{Float64})::Vector{Float64}`, where both the input and output vectors have length two. The function `create_planar_mvf` returns a multivector field `mvf` on `lc`, which can then be further analyzed using for example the function `connection_matrix`.

The input data `lc` and `coords` can be generated using one of the following methods:

  * `create_cubical_rectangle`
  * `create_simplicial_rectangle`
  * `create_simplicial_delaunay`

In each case, the provided coordinate vector can be transformed to the correct bounding box values using the conversion function `convert_planar_coordinates`.

# Example 1

Suppose we define a sample vector field using the commands

```julia
function samplevf(x::Vector{Float64})
    #
    # Sample vector field with nontrivial Morse decomposition
    #
    x1, x2 = x
    y1 = x1 * (1.0 - x1*x1 - 3.0*x2*x2)
    y2 = x2 * (1.0 - 3.0*x1*x1 - x2*x2)
    return [y1, y2]
end
```

One first creates a triangulation of the enclosing box, which in this case is given by `[-2,2] x [-2,2]` using the commands

```julia
n = 21
lc, coords = create_simplicial_rectangle(n,n);
coordsN = convert_planar_coordinates(coords,[-2.0,-2.0],[2.0,2.0]);
```

The multivector field is then generated using

```julia
mvf = create_planar_mvf(lc,coordsN,samplevf);
```

and the commands

```julia
cm = connection_matrix(lc, mvf);
cm.conley
full_from_sparse(cm.matrix)
```

finally show that this vector field gives rise to a Morse decomposition with nine Morse sets, and twelve connecting orbits. Using the commands

```julia
fname = "morse_test.pdf"
plot_planar_simplicial_morse(lc, coordsN, fname, cm.morse, pv=true)
```

these Morse sets can be visualized. The image will be saved in `fname`.

# Example 2

An example with periodic orbits can be generated using the vector field

```julia
function samplevf2(x::Vector{Float64})
    #
    # Sample vector field with nontrivial Morse decomposition
    #
    x1, x2 = x
    c0 = x1*x1 + x2*x2
    c1 = (c0 - 4.0) * (c0 - 1.0)
    y1 = -x2 + x1 * c1
    y2 =  x1 + x2 * c1
    return [-y1, -y2]
end
```

The Morse decomposition can now be computed via

```julia
n2 = 51
lc2, coords2 = create_cubical_rectangle(n2,n2);
coords2N = convert_planar_coordinates(coords2,[-4.0,-4.0],[4.0,4.0]);
mvf2 = create_planar_mvf(lc2,coords2N,samplevf2);
cm2 = connection_matrix(lc2, mvf2);
cm2.conley
cm2.poset
full_from_sparse(cm2.matrix)

fname2 = "morse_test2.pdf"
plot_planar_cubical_morse(lc2, fname2, cm2.morse, pv=true)
```

In this case, one obtains three Morse sets: One is a stable equilibrium, one is an unstable periodic orbit, and the last is a stable periodic orbit.
