```
hardware_transform_atoms(atoms,device_capabilities::DeviceCapabilities=get_device_capabilities())
```

Given the constraints of the hardware from `device_capabilities` (specifically the position resolution) and an iterable containing the atom positions `atoms`, returns a Tuple containing the adjusted  atom positions the machine is capable of resolving and the mean squared error between the  desired atom positions and newly generated ones.

Note that other constraints such as the maximum width, height, and minimum supported spacings are not taken into account in adjusting the atoms. This may result in the [`validation`](@ref)  function failing and requiring user intervention to modify the atom positions such that  they satisfy the other constraints.

# Examples

```jldoctest;
julia> atom_positions = ((1.12,), (2.01,), (3.01,));

julia> hardware_transform_atoms(atom_positions) # by default, calls get_device_capabilities()
([(1.1,), (2.0,), (3.0,)], 0.013333333333333197)
```
