```
LinearChain(;
        ions, comfrequencies::NamedTuple{(:x,:y,:z)},
        selectedmodes::NamedTuple{(:x,:y,:z), N::Int=10
    )
```

Generates and stores all of the information necessary to describe a collection of ions trapped  in a 3D harmonic potential and forming a linear coulomb crystal. Relevant to calculating the normal mode structure of the linear chain is the charge, mass  and ordering of the ions.

**user-defined fields**

  * `ions`: An iterable list of ions that compose the linear Coulomb crystal
  * `comfrequencies::NamedTuple{(:x,:y,:z)`: Describes the COM frequencies    `(x=ν_x, y=ν_y, z=ν_z)`. The z-axis is taken to be along the crystal's axis of    symmetry. Note that these only correspond to true COM modes if all ions have the same   mass, otherwise this is a misnomer and corresponds to the smallest (largest) eigenfrequency   mode in the axial (radial) directions. Note: we assume that `ν_x > ν_y > ν_z`.
  * `selectedmodes::NamedTuple{(:x,:y,:z)}`:  e.g. `selectedmodes=(x=[1], y=[1, 2:3], z=[:])`.   Specifies the axis and a list of integers which correspond to the $i^{th}$ farthest   mode away from the COM (see note above about meaning of "COM") for that axis. For example,    `selectedmodes=(z=[2])` would specify the axial stretch mode. These are the modes that will    be modeled in the chain.Note: `selectedmodes=(x=[],y=[],z=[1])`, `selectedmodes=(y=[],z=[1])`   and `selectedmodes=(;z=[1])` are all acceptable and equivalent.
  * `N::Int=10`: Optionally specify the Hilbert space dimension for each normal mode.

**derived fields**

  * `ionpositions::Vector{<:Real}`: The relative positions of the ions in meters.
