`UnitCell{T}` is a data type representing a general unit cell of a lattice.

# Attributes

  * `primitives  :: Vector{ Vector{ Float64 } }`: primitive bases vectors of the lattice.
  * `basis       :: Vector{ Vector{ Float64 } }`: positions of the sub-lattices.
  * `bonds       :: Vector{Bond{T}}`: the set of all bonds defining a lattice.
  * `fields      :: Vector{ Vector{Float64}}` : the fields oneach basis site.
  * `localDim    :: Int64`: Local Hilbert space dimension ( e.g. 3 for classical spins, 2 for spin-1/2 electrons ).
  * `BC          :: Vector{ ComplexF64 }`: boundary conditions, in the form of [e^{ιθ_i}]. e.g. θ=0 for PBC, θ=π for APBC, and so on.

Initialize this structure using 

```julia
UnitCell( as::Vector{Vector{Float64}} , localDim::Int64)
UnitCell( as::Vector{Vector{Float64}} , localDim::Int64, rank::Int64)
```
