```
GeneralLattice{D,K,T} <: AbstractLattice{D}
GeneralLattice(vectors, sites)
```

The general lattice type for tiling the space. Type parameter `D` is the dimension, `K` is the number of sites in a unit cell and `T` is the data type for coordinates, e.g. `Float64`. Input arguments are

  * `vectors` is a vector/tuple of D-tuple. Its length is D, it specifies the Bravais lattice vectors.
  * `sites` is a vector/tuple of D-tuple. Its length is K, it specifies the sites inside a Bravais cell.
