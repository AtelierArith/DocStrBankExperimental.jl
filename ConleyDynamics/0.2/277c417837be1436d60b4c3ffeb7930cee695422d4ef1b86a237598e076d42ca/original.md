```
create_simplicial_rectangle(nx::Int, ny::Int; p::Int=2)
```

Create a simplicial complex covering a rectangle in the plane. The complex is over the rationals if `p=0`, and over `GF(p)` if `p>0`.

The rectangle is given by the subset `[0,nx] x [0,ny]` of the plane. Each unit square is represented by four triangles, which meet in the center point of the square. Labels have the following meaning:

  * The label `XXXYYYb` corresponds to the point `(XXX, YYY)`.
  * The label `XXXYYYc` corresponds to `(XXX + 1/2, YYY + 1/2)`.

The number of characters in `XXX` and `YYY` matches the number  of digits of the larger number of `nx` and `ny`. The function returns the following objects:

  * A simplicial complex `sc::LefschetzComplex`.
  * A vector `coords::Vector{Vector{Float64}}` of vertex coordinates.
