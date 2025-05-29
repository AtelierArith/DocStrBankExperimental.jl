A `Frame` holds data for one step of a simulation. As not all formats provide all the types of information, some fields may be initialized to a default value. A `Frame` may contain the following data:

  * Positions for all the atoms in the system;
  * Velocities for all the atoms in the system;
  * The [`Topology`](@ref) of the system;
  * The [`UnitCell`](@ref) of the system.
