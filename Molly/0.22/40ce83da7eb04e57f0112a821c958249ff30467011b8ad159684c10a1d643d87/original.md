```
ReplicaSystem(; <keyword arguments>)
```

A wrapper for replicas in a replica exchange simulation.

Each individual replica is a [`System`](@ref). Properties unused in the simulation or in analysis can be left with their default values. The minimal required arguments are `atoms`, `replica_coords`, `boundary` and `n_replicas`. `atoms` and the elements in `replica_coords` should have the same length, along with `atoms_data` and the elements in `replica_velocities` if these are provided. The number of elements in `replica_coords`, `replica_velocities`, `replica_loggers` and the interaction arguments `replica_pairwise_inters`, `replica_specific_inter_lists`, `replica_general_inters` and `replica_constraints` should be equal to `n_replicas`. This is a sub-type of `AbstractSystem` from AtomsBase.jl and implements the interface described there.

When using `ReplicaSystem` with [`CellListMapNeighborFinder`](@ref), the number of threads used for both the simulation of replicas and the neighbor finder should be set to be the same. This can be done by passing `nbatches=(min(n, 8), n)` to [`CellListMapNeighborFinder`](@ref) during construction where `n` is the number of threads to be used per replica.

# Arguments

  * `atoms::A`: the atoms, or atom equivalents, in the system. Can be   of any type but should be a bits type if the GPU is used.
  * `replica_coords`: the coordinates of the atoms in each replica.
  * `boundary::B`: the bounding box in which the simulation takes place.
  * `n_replicas::Integer`: the number of replicas of the system.
  * `replica_velocities=[zero(replica_coords[1]) * u"ps^-1" for _ in 1:n_replicas]`:   the velocities of the atoms in each replica.
  * `atoms_data::AD`: other data associated with the atoms, allowing the atoms to   be bits types and hence work on the GPU.
  * `topology::TO=nothing`: topological information about the system such as which   atoms are in the same molecule (to be used if the same for all replicas).   This is only used if no value is passed to the argument `replica_topology`.
  * `replica_topology=[nothing for _ in 1:n_replicas]`: the topological information for   each replica.
  * `pairwise_inters=()`: the pairwise interactions in the system, i.e. interactions   between all or most atom pairs such as electrostatics (to be used if the same for all replicas).   Typically a `Tuple`. This is only used if no value is passed to the argument   `replica_pairwise_inters`.
  * `replica_pairwise_inters=[() for _ in 1:n_replicas]`: the pairwise interactions for   each replica.
  * `specific_inter_lists=()`: the specific interactions in the system, i.e. interactions   between specific atoms such as bonds or angles (to be used if the same for all replicas).   Typically a `Tuple`. This is only used if no value is passed to the argument   `replica_specific_inter_lists`.
  * `replica_specific_inter_lists=[() for _ in 1:n_replicas]`: the specific interactions in   each replica.
  * `general_inters=()`: the general interactions in the system, i.e. interactions involving   all atoms such as implicit solvent (to be used if the same for all replicas). Each should   implement the AtomsCalculators.jl interface. Typically a `Tuple`. This is only used if no   value is passed to the argument `replica_general_inters`.
  * `replica_general_inters=[() for _ in 1:n_replicas]`: the general interactions for   each replica.
  * `constraints::CN=()`: the constraints for bonds and angles in the system (to be used if the same   for all replicas). Typically a `Tuple`. This is only used if no value is passed to the   argument `replica_constraints`.
  * `replica_constraints=[() for _ in 1:n_replicas]`: the constraints for bonds and angles in each   replica.
  * `neighbor_finder::NF=NoNeighborFinder()`: the neighbor finder used to find   close atoms and save on computation. It is duplicated for each replica.
  * `replica_loggers=[() for _ in 1:n_replicas]`: the loggers for each replica   that record properties of interest during a simulation.
  * `exchange_logger::EL=ReplicaExchangeLogger(n_replicas)`: the logger used to record   the exchange of replicas.
  * `force_units::F=u"kJ * mol^-1 * nm^-1"`: the units of force of the system.   Should be set to `NoUnits` if units are not being used.
  * `energy_units::E=u"kJ * mol^-1"`: the units of energy of the system. Should   be set to `NoUnits` if units are not being used.
  * `k::K=Unitful.k` or `Unitful.k * Unitful.Na`: the Boltzmann constant, which may be   modified in some simulations. `k` is chosen based on the `energy_units` given.
  * `data::DA=nothing`: arbitrary data associated with the replica system.
