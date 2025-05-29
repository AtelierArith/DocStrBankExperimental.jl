```
MonteCarloAnisotropicBarostat(pressure, temperature, boundary; n_steps=30,
                   n_iterations=1, scale_factor=0.01, scale_increment=1.1,
                   max_volume_frac=0.3, trial_find_neighbors=false)
```

The Monte Carlo anisotropic barostat for controlling pressure.

For 3D systems, `pressure` is a `SVector` of length 3 with components pressX, pressY, and pressZ representing the target pressure in each axis. For 2D systems, `pressure` is a `SVector` of length 2 with components pressX and pressY. To keep an axis fixed, set the corresponding pressure to `nothing`.

See [Chow and Ferguson 1995](https://doi.org/10.1016/0010-4655(95)00059-O), [Åqvist et al. 2004](https://doi.org/10.1016/j.cplett.2003.12.039) and the OpenMM source code. At regular intervals a Monte Carlo step is attempted by scaling the coordinates and the bounding box by a randomly chosen amount in a randomly selected axis. The step is accepted or rejected based on

$$
\Delta W = \Delta E + P \Delta V - N k_B T \ln \left( \frac{V + \Delta V}{V} \right)
$$

where `ΔE` is the change in potential energy, `P` is the equilibrium pressure along the selected axis, `ΔV` is the change in volume, `N` is the number of molecules in the system, `T` is the equilibrium temperature and `V` is the system volume. If `ΔW ≤ 0` the step is always accepted, if `ΔW > 0` the step is accepted with probability `exp(-ΔW/kT)`.

The scale factor is modified over time to maintain an acceptance rate of around half. If the topology of the system is set then molecules are moved as a unit so properties such as bond lengths do not change.

The barostat assumes that the simulation is being run at a constant temperature but does not actively control the temperature. It should be used alongside a temperature coupling method such as the [`Langevin`](@ref) simulator or [`AndersenThermostat`](@ref) coupling. The neighbor list is not updated when making trial moves or after accepted moves. Note that the barostat can change the bounding box of the system.
