```
MollyCalculator(; <keyword arguments>)
```

A calculator for use with the AtomsCalculators.jl interface.

`neighbors` can optionally be given as a keyword argument when calling the calculation functions to save on computation when the neighbors are the same for multiple calls. In a similar way, `n_threads` can be given to determine the number of threads to use when running the calculation function. Note that this calculator is designed for using Molly in other contexts; if you want to use another calculator in Molly it can be given as `general_inters` when creating a [`System`](@ref).

Not currently compatible with virial calculation. Not currently compatible with using atom properties such as `σ` and `ϵ`.

# Arguments

  * `pairwise_inters::PI=()`: the pairwise interactions in the system, i.e.   interactions between all or most atom pairs such as electrostatics.   Typically a `Tuple`.
  * `specific_inter_lists::SI=()`: the specific interactions in the system,   i.e. interactions between specific atoms such as bonds or angles. Typically   a `Tuple`.
  * `general_inters::GI=()`: the general interactions in the system,   i.e. interactions involving all atoms such as implicit solvent. Each should   implement the AtomsCalculators.jl interface. Typically a `Tuple`.
  * `neighbor_finder::NF=NoNeighborFinder()`: the neighbor finder used to find   close atoms and save on computation.
  * `force_units::F=u"kJ * mol^-1 * nm^-1"`: the units of force of the system.   Should be set to `NoUnits` if units are not being used.
  * `energy_units::E=u"kJ * mol^-1"`: the units of energy of the system. Should   be set to `NoUnits` if units are not being used.
  * `k::K=Unitful.k` or `Unitful.k * Unitful.Na`: the Boltzmann constant, which may be   modified in some simulations. `k` is chosen based on the `energy_units` given.
  * `dims::Integer=3`: the number of dimensions in the system.
