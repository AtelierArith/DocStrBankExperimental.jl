`Model` is a data type representing a general Tight Binding system.

# Attributes

  * `uc      ::  UnitCell`: the Unit cell of the lattice.
  * `bz      ::  BZ`: The discretized Brillouin Zone.
  * `Ham     ::  Hamiltonian`: the Hamiltonian at all momentum-points.
  * `T       ::  Float64`: the temperature of the system.
  * `filling ::  Float64`: The filling of the system.
  * `mu      ::  Float64`: The chemical potential of the system.
  * `stat    ::  Int64` : ±1 for bosons and fermions.
  * `gap     ::  Float64` : the energy gap of excitations at the given filling.
  * `Gk      ::  Array{Matrix{ComplexF64}}` : An array (corresponding to the grid of k-points in `BZ`) of Greens functions.

Initialize this structure using 

```julia
Model(uc::UnitCell, bz::BZ, Ham::Hamiltonian ; T::Float64=1e-3, filling::Float64=-1.0, mu::Float64=0.0, stat::Int64=-1)
```

You can either input a filling, or a chemical potential. The corresponding μ for a given filling, or filling for a given μ is automatically calculated.
