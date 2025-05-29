```
kepler_solver(M, e) -> E
```

### Purpose

Solve Kepler's equation in the elliptic motion regime ($0 ≤ e ≤ 1$) and return eccentric anomaly $E$.

### Explanation

In order to find the position of a body in elliptic motion (e.g., in the two-body problem) at a given time $t$, one has to solve the [Kepler's equation](https://en.wikipedia.org/wiki/Kepler%27s_equation)

$$
M(t) = E(t) - e \sin E(t)
$$

where $M(t) = (t - t_0)/P$ is the mean anomaly, $E(t)$ the eccentric anomaly, $e$ the eccentricity of the orbit, $t_0$ is the time of periapsis passage, and $P$ is the period of the orbit.  Usually the eccentricity is given and one wants to find the eccentric anomaly $E(t)$ at a specific time $t$, so that also the mean anomaly $M(t)$ is known.

### Arguments

  * `M`: mean anomaly.
  * `e`: eccentricity, in the elliptic motion regime ($0 ≤ e ≤ 1$)

### Output

The eccentric anomaly $E$, restricted to the range $[-π, π]$.

### Method

Many different numerical methods exist to solve Kepler's equation.  This function implements the algorithm proposed in Markley (1995) Celestial Mechanics and Dynamical Astronomy, 63, 101 (DOI:[10.1007/BF00691917](http://dx.doi.org/10.1007/BF00691917)).  This method is not iterative, requires only four transcendental function evaluations, and has been proved to be fast and efficient over the entire range of elliptic motion $0 ≤ e ≤ 1$.

### Example

  * Find the eccentric anomaly for an orbit with eccentricity $e = 0.7$ and for $M(t) = 8π/3$.

    ```jldoctest
    julia> using AstroLib

    julia> ecc = 0.7;

    julia> E = kepler_solver(8pi/3, ecc)
    2.5085279492864223
    ```
  * Plot the eccentric anomaly as a function of mean anomaly for eccentricity $e = 0, 0.5, 0.9$.  Recall that `kepler_solver` gives $E ∈ [-π, π]$, use `mod2pi` to have it in $[0, 2π]$.  Use [Plots.jl](https://github.com/JuliaPlots/Plots.jl/) for plotting.

    ```julia
    using AstroLib
    using Plots
    M = range(0, stop=2pi, length=1001)[1:end-1];
    for ecc in (0, 0.5, 0.9)
        plot(M, mod2pi.(kepler_solver.(M, ecc)))
    end
    ```

### Notes

The true anomaly can be calculated with `trueanom` function.
