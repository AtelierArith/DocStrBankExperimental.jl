```
planar_nontransverse_edges(lc::LefschetzComplex, coords::Vector{Vector{Float64}}, vf;
                           npts::Int=100)
```

Find all edges of a planar Lefschetz complex which are not flow transverse.

The Lefschetz complex is given in `lc`, the coordinates of all vertices of the complex in `coords`, and the vector field is specified in `vf`. The optional parameter `npts` determines how many points along an edge are evaluated for the transversality check. The function returns a list of nontransverse edges as `Vector{Int}`, which contains the edge indices.
