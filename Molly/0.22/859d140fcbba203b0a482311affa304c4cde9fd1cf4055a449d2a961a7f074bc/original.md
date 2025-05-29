```
MonteCarloMembraneBarostat(pressure, tension, temperature, boundary; n_steps=30,
                   n_iterations=1, scale_factor=0.01, scale_increment=1.1,
                   max_volume_frac=0.3, trial_find_neighbors=false,
                   xy_isotropy=false, z_axis_fixed=false, constant_volume=false)
```

The Monte Carlo membrane barostat for controlling pressure.

Set the `xy_isotropy` flag to `true` to scale the x and y axes isotropically. Set the `z_axis_fixed` flag to `true` to uncouple the z-axis and keep it fixed. Set the `constant_volume` flag to `true` to keep the system volume constant by scaling the z-axis accordingly. The `z_axis_fixed` and `constant_volume` flags cannot be `true` simultaneously.

See [Chow and Ferguson 1995](https://doi.org/10.1016/0010-4655(95)00059-O), [Åqvist et al. 2004](https://doi.org/10.1016/j.cplett.2003.12.039) and the OpenMM source code. At regular intervals a Monte Carlo step is attempted by scaling the coordinates and the bounding box by a randomly chosen amount in a randomly selected axis. The step is accepted or rejected based on

$$
\Delta W = \Delta E + P \Delta V - \gamma \Delta A - N k_B T \ln \left( \frac{V + \Delta V}{V} \right)
$$

where `ΔE` is the change in potential energy, `P` is the equilibrium pressure along the selected axis, `ΔV` is the change in volume, `γ` is the surface tension, `ΔA` is the change in surface area, `N` is the number of molecules in the system, `T` is the equilibrium temperature and `V` is the system volume. If `ΔW ≤ 0` the step is always accepted, if `ΔW > 0` the step is accepted with probability `exp(-ΔW/kT)`.

The scale factor is modified over time to maintain an acceptance rate of around half. If the topology of the system is set then molecules are moved as a unit so properties such as bond lengths do not change.

The barostat assumes that the simulation is being run at a constant temperature but does not actively control the temperature. It should be used alongside a temperature coupling method such as the [`Langevin`](@ref) simulator or [`AndersenThermostat`](@ref) coupling. The neighbor list is not updated when making trial moves or after accepted moves. Note that the barostat can change the bounding box of the system.

This barostat is only available for 3D systems.
