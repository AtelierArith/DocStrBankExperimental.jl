```
trueanom(E, e) -> true anomaly
```

### Purpose

Calculate true anomaly for a particle in elliptic orbit with eccentric anomaly $E$ and eccentricity $e$.

### Explanation

In the two-body problem, once that the [Kepler's equation](https://en.wikipedia.org/wiki/Kepler%27s_equation) is solved and $E(t)$ is determined, the polar coordinates $(r(t), θ(t))$ of the body at time $t$ in the elliptic orbit are given by

$$
θ(t) = 2 \arctan \left( \sqrt{\frac{1 + e}{1 - e}} \tan\frac{E(t)}{2} \right)
$$

$$
r(t) = \frac{a(1 - e^2)}{1 + e\cos(θ(t) - θ_0)}
$$

in which $a$ is the semi-major axis of the orbit, and $θ_0$ the value of angular coordinate at time $t = t_0$.

### Arguments

  * `E`: eccentric anomaly.
  * `e`: eccentricity, in the elliptic motion regime ($0 ≤ e ≤ 1$)

### Output

The true anomaly.

### Example

Plot the true anomaly as a function of mean anomaly for eccentricity $e = 0, 0.5, 0.9$. Use [Plots.jl](https://github.com/JuliaPlots/Plots.jl/) for plotting.

```julia
using Plots
M = range(0, stop=2pi, length=1001)[1:end-1];
p = plot()
for ecc in (0, 0.5, 0.9)
    plot!(p, M, mod2pi.(trueanom.(kepler_solver.(M, ecc), ecc)))
end
p
```

### Notes

The eccentric anomaly can be calculated with [`kepler_solver`](@ref) function.
