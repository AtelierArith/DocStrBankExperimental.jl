```
Lattice
```

A Julia constructor for a lattice object. The lattice object is used to define the geometry of the lattice. `Nx` and `Ny` are the number of sites in the x and y directions, respectively. `N` is the total number of sites. `lin_idx` is a `LinearIndices` object and `car_idx` is a `CartesianIndices` object, and they are used to efficiently select sites on the lattice.
