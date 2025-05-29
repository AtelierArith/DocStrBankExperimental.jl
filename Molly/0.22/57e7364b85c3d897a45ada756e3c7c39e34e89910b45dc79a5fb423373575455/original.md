```
AndersenThermostat(temperature, coupling_const)
```

The Andersen thermostat for controlling temperature.

The velocity of each atom is randomly changed each time step with probability `dt / coupling_const` to a velocity drawn from the Maxwell-Boltzmann distribution. See [Andersen 1980](https://doi.org/10.1063/1.439486).
