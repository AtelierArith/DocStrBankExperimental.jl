```
add_thermal_noise(sim::AbstractSim, Temp::NumberOrArrayOrFunction; name="thermal", scaling=t -> 1.0, k_B=k_B)
```

Adds thermal noise fields to the simulation. For micromagnetic model, the thermal noise is defined as

$$
\mathbf{b}^u = \eta \sqrt \frac{2 \alpha k_B T}{\mu_0 M_s \gamma \Delta V dt}
$$

and $\eta$ is a random number follows the normal distribution where $\gamma=2.211\times 10^5$ m/(A·s) is the gyromagnetic ratio.

For the atomistic model, the thermal noise is defined as

$$
\mathbf{b}^u = \eta \sqrt \frac{2 \alpha k_B T}{\gamma \mu_s dt}.
$$

where $\eta$ is a random number follows the normal distribution and $\gamma=1.76\times 10^{11}$ rad/(T·s). 

### Arguments

  * `sim::AbstractSim`: The simulation object.
  * `Temp::NumberOrArrayOrFunction`: Temperature value (can be a constant, array, or function).
  * `name::String`: Name for the noise field (default: `"thermal"`).
  * `scaling::Function`: A function to scale the noise over time (default: `t -> 1.0`).
  * `k_B::Float64`: Boltzmann constant (default: `k_B`).

### Example

```julia
# Add thermal noise with a constant temperature of 100 K and a scaling function
add_thermal_noise(sim, 100.0, scaling = t -> exp(-t/1e-9))
```
