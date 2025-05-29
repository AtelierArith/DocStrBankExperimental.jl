```
reverse_mc(dim::Int, n::Int, ρ::Float64, g2_targ::Function; initial_box = missing, bin_size = 0.05, range = 5, sweeps = 100, displace = 0.1, t_i = 1, t_f = 0.001, cooling_rate = 0.98)
```

Reverse Monte Carlo algorithm to generate equilibrium configurations that yield a target pair correlation function $g_2(r)$.

# Arguments

  * `dim::Int`: Dimensionality of the system.
  * `n::Int`: Number of particles.
  * `ρ::Float64`: Number density of the particles.
  * `g2_targ::Function`: Target pair correlation function as a function `g2_targ(r)`.

# Keyword arguments

  * `initial_box::Box` (optional): Initial configuration box. Default is `missing` which generates a random box.
  * `bin_size::Float64` (optional): Bin size for computing the pair correlation function. Default is 0.05.
  * `range::Float64` (optional): Range for the interaction potential. Default is 5.
  * `sweeps::Int` (optional): Number of Monte Carlo sweeps at each temprature. Default is 100.
  * `displace::Float64` (optional): Maximum displacement for particle moves. Default is 0.1.
  * `t_i::Float64` (optional): Initial temperature. Default is 1.
  * `t_f::Float64` (optional): Final temperature. Default is 0.001.
  * `cooling_rate::Float64` (optional): Cooling rate for temperature reduction. Default is 0.98.

# Returns

  * `b::Box`: Generated equilibrium classical configuration box. Use `b.particles'` to get the particle positions.

# Example

```
box = InverseStatMech.reverse_mc(2, 100, 0.5, r -> 1 - exp(-π*r^2))
```
