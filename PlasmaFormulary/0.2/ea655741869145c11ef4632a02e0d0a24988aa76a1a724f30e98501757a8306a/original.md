```
thermal_speed(T::EnergyOrTemp, mass::Mass, method::ThermalVelocityMethod = MostProbable(), ndim = 3)
```

Calculate the speed of thermal motion for particles with a Maxwellian distribution.

$$
v_{th} = C_o \sqrt{\frac{k_B T}{m}}
$$

where $T$ is the temperature associated with the distribution, $m$ is the particle's mass, and $C_o$ is a constant of proportionality. ```
