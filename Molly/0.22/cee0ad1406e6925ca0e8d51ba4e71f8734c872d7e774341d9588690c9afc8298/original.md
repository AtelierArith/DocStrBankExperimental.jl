```
RescaleThermostat(temperature)
```

The velocity rescaling thermostat for controlling temperature.

Velocities are immediately rescaled to match a target temperature. The scaling factor for the velocities each step is

$$
\lambda = \sqrt{\frac{T_0}{T}}
$$

This thermostat should be used with caution as it can lead to simulation artifacts.
