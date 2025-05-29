```
System(; <keyword arguments>)
```

A physical system to be simulated.

Properties unused in the simulation or in analysis can be left with their default values. The minimal required arguments are `atoms`, `coords` and `boundary`. `atoms` and `coords` should have the same length, along with `velocities` and `atoms_data` if these are provided. This is a sub-type of `AbstractSystem` from AtomsBase.jl and implements the interface described there.

# Arguments

  * `atoms::A`: the atoms, or atom equivalents, in the system. Can be   of any type but should be a bits type if the GPU is used.
  * `coords::C`: the coordinates of the atoms in the system. Typically a   vector of `SVector`s of 2 or 3 dimensions.
  * `boundary::B`: the bounding box in which the simulation takes place.
  * `velocities::V=zero(coords) * u"ps^-1"`: the velocities of the atoms in the   system.
  * `atoms_data::AD=[]`: other data associated with the atoms, allowing the atoms to   be bits types and hence work on the GPU.
  * `topology::TO=nothing`: topological information about the system such as which   atoms are in the same molecule.
  * `pairwise_inters::PI=()`: the pairwise interactions in the system, i.e.   interactions between all or most atom pairs such as electrostatics.   Typically a `Tuple`.
  * `specific_inter_lists::SI=()`: the specific interactions in the system,   i.e. interactions between specific atoms such as bonds or angles. Typically   a `Tuple`.
  * `general_inters::GI=()`: the general interactions in the system,   i.e. interactions involving all atoms such as implicit solvent. Each should   implement the AtomsCalculators.jl interface. Typically a `Tuple`.
  * `constraints::CN=()`: the constraints for bonds and angles in the system.   Typically a `Tuple`.
  * `neighbor_finder::NF=NoNeighborFinder()`: the neighbor finder used to find   close atoms and save on computation.
  * `loggers::L=()`: the loggers that record properties of interest during a   simulation.
  * `force_units::F=u"kJ * mol^-1 * nm^-1"`: the units of force of the system.   Should be set to `NoUnits` if units are not being used.
  * `energy_units::E=u"kJ * mol^-1"`: the units of energy of the system. Should   be set to `NoUnits` if units are not being used.
  * `k::K=Unitful.k` or `Unitful.k * Unitful.Na`: the Boltzmann constant, which may be   modified in some simulations. `k` is chosen based on the `energy_units` given.
  * `data::DA=nothing`: arbitrary data associated with the system.
