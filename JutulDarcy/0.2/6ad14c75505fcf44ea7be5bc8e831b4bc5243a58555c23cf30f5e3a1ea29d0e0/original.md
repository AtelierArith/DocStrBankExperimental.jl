```
reservoir_domain(g; permeability = convert_to_si(0.1, :darcy), porosity = 0.1, kwarg...)
```

Set up a `DataDomain` instance for given mesh or other representation `g`. `permeability` and `porosity` are then added to the domain. If scalars are passed, they are expanded to cover all cells. Arrays are asserted to match all cells. Permeability is either one value per cell (diagonal scalar), one value per dimension given in each row (for a diagonal tensor) or a vector that represents a compact full tensor representation (6 elements in 3D, 3 in 2D).

# Default data and their values

|                         Name |                                Explanation |       Unit | Default |
| ----------------------------:| ------------------------------------------:| ----------:| -------:|
|               `permeability` |         Rock ability to conduct fluid flow |      $m^2$ |  100 mD |
|                   `porosity` |   Rock void fraction open to flow (0 to 1) |          - |     0.3 |
|               `rock_density` |                       Mass density of rock | $kg^3/m^3$ |  2000.0 |
|         `rock_heat_capacity` |             Specific heat capacity of rock | $J/(kg K)$ |   900.0 |
|  `rock_thermal_conductivity` |                  Heat conductivity of rock |    $W/m K$ |     3.0 |
| `fluid_thermal_conductivity` |          Heat conductivity of fluid phases |    $W/m K$ |     0.6 |
|    `component_heat_capacity` | Specific heat capacity of fluid components | $J/(kg K)$ |  4184.0 |

Note that the default values are taken to be roughly those of water for fluid phases and sandstone for those of rock. Choice of values can severely impact your simulation results - take care to check the values that your physical system makes use of!

# Optional values

|                          Name |                               Explanation |    Unit | Default |
| -----------------------------:| -----------------------------------------:| -------:| -------:|
|                `net_to_gross` |   Magnitude of porosity available to flow |       - |     1.0 |
|                   `diffusion` |  Diffusion coefficient for each component | $m^2/s$ |     0.0 |
|   `transmissibility_override` |   Transmissibility override for each face |   $m^2$ |     NaN |
| `transmissibility_multiplier` | Transmissibility multiplier for each face |       - |     1.0 |

These values are optional and will only be added if specified. For e.g. net-to-gross and transmissibility multipliers a default value of 1.0 will be assumed in the code if it is not present.

The transmissibility override can be used to override the transmissibility calculated from geometry and other properties. This is useful for example if you have an externally computed model. The values must be given for every face on the mesh. Values that are NaN or Inf will be treated as missing and the standard transmissibility calculator will be used instead for those faces.
