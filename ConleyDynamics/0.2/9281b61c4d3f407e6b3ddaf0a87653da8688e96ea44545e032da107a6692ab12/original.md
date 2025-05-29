```
create_simplicial_delaunay(boxw::Real, boxh::Real, pdist::Real, attmpt::Int;
                           p::Int=2)
```

Create a planar Delaunay triangulation inside a box. The complex is over the rationals if `p=0`, and over `GF(p)` if `p>0`.

The function selects a random sample of points inside the rectangular box `[0,boxw] x [0,boxh]`, while trying to maintain a minimum distance  of `pdist` between the points. The argument `attmpt` specifies the number of attempts when trying to add points. A standard value is 20, and larger values tend to fill holes better, but at the expense of runtime. From the random sample, the function then creates a Delaunay triangulation, and returns the following objects:

  * A simplicial complex `sc::LefschetzComplex`.
  * A vector `coords::Vector{Vector{Float64}}` of vertex coordinates.

Note that the function does not provide a full triangulation of the given rectangle. Close to the boundary there will be gaps.
