```
BerendsenThermostat(temperature, coupling_const)
```

The Berendsen thermostat for controlling temperature.

The scaling factor for the velocities each step is

$$
\lambda^2 = 1 + \frac{\delta t}{\tau} \left( \frac{T_0}{T} - 1 \right)
$$

This thermostat should be used with caution as it can lead to simulation artifacts.
