```
Lattice{T <: Real}
```

Data type of lattice.

# Fields

  * `lattice::Array{T, 2}`: stores 3×3 matrix for the lattice
  * `a:Array{T, 1}`: stores basis of axis a
  * `b:Array{T, 1}`: stores basis of axis b
  * `c:Array{T, 1}`: stores basis of axis c
