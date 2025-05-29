`Bond{T}` is a data type representing a general bond on a lattice.

# Attributes

  * `base::Int64`: sub-lattice of the initial site on the bond.
  * `target::Int64`: sub-lattice of the final site on the bond.
  * `offset::Vector{Int64}`: the difference of the unit cells in which these sublattices belong to, in units of the lattice basis vectors.
  * `mat::Array{ComplexF64, T}`: an array describing this bond –> can be hopping for partons, or spin-exchange for spins. The rank of the array, `T`, is determined by the specific  model being looked at. Eg. rank = 2 for a free parton Hamiltonian.
  * `dist::Float64`: the distance b/w the two sites = length of bond.
  * `label::String`: some string label to mark the bond type.
