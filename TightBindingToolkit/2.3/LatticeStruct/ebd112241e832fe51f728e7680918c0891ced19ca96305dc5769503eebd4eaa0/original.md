`Lattice{T}` is a data type representing a general real-space lattice constructed out of a `UnitCell{T}`.

# Attributes

  * `uc          ::  UnitCell{T}`: Unit Cell of the lattice.
  * `size        ::  Vector{Int64}`: size of the lattice in units of the UnitCell `primitives`.
  * `length      ::  Int64`: total number of sites.
  * `sites       ::  Dict{ Tuple{Int64, Vector{Int64}}, Int64}` : a dictionary with key = (sublattice, offset), and the corresponding value being the site number on the lattice.
  * `positions   ::  Vector{ Vector{Float64}}`: real-space positions of all the lattice sites.
  * `fields      ::  Vector{ Vector{Float64}}`: the fields on all the lattice sites.
  * `bondSites   ::  Matrix{Int64}`: a matrix with `lattice.length` rows such that `bondSites[s, i]` is the site number of the ith neighbour of site-s on the lattice.
  * `bondDists   ::  Matrix{Float64}`: a matrix with `lattice.length` rows such that `bondDists[s, i]` is the distance to the ith neighbour of site-s on the lattice.
  * `bondLabels  ::  Matrix{String}`: a matrix with `lattice.length` rows such that `bondLabels[s, i]` is the label of the bond to the ith neighbour of site-s on the lattice.
  * `bondMats    ::  Matrix{Array{ComplexF64, T}}`: a matrix with `lattice.length` rows such that `bondMats[s, i]` is the `Array{ComplexF64, T}` of the bond connecting to the ith neighbour of site-s on the lattice.

Initialize this structure using 

```julia
Lattice( uc::UnitCell{T}, size::Vector{Int64} ; null_dist::Float64 = -1.0, null_label::String = "-")
```

where `null_dist` and `null_label` are used for bonds which are not allowed due to given boundary conditions, but still tracked in the code.
