```
create_cubical_box(nx::Int, ny::Int, nz::Int;
                   p::Int=2, randomize::Real=0.0)
```

Create a cubical complex covering a box in space. The complex is over the rationals if `p=0`, and over `GF(p)` if `p>0`.

The box is given by the subset `[0,nx] x [0,ny] x [0,nz]` of space, and each unit cube gives a three-dimensional cube in the resulting cubical complex. The function returns the following objects:

  * A cubical complex `cc::LefschetzComplex`
  * A vector `coords::Vector{Vector{Float64}}` of vertex coordinates

If the optional parameter `randomize` is assigned a positive real fraction `r` less that 0.5, then the actual coordinates will be randomized. They are chosen uniformly from balls of radius `r` centered at each vertex.
