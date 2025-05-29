```
optim_parametrized_pot(my_params, pot, dim, ρ, targ_g2, targ_s; 
    large_r_grid = missing, n::Int = 600, bin_size::Float64 = 0.05, r_range::Float64 = 10, k_range::Float64 = 10,
    g2_weight_range::Float64 = 2, s_weight_range::Float64 = 4, 
    n_threads::Int = 15, configs_per_thread::Int = 10, displace = 0.2, Ψ_tol::Float64 = 0.005, show_pb::Bool = true, test::Bool = false)
```

Using the Torquato-Wang algorithm to perform iterative optimization of potential parameters to match target pair correlation function and structure factor.

## Arguments

  * `my_params::Vector{Float64}`: Vector of initial potential parameters.
  * `pot::Function`: Potential function that calculates the interaction potential between particles.
  * `dim::Int`: Dimension of the system.
  * `ρ::Float64`: Density of the system.
  * `targ_g2::Function`: Function representing the target pair correlation function. Accepts a distance value `r` and returns the target g2 value at that distance.
  * `targ_s::Function`: Function representing the target structure factor. Accepts a wave vector `k` and returns the target S value at that wave vector.

## Keyword Arguments (all are optional)

  * `large_r_grid::Missing`: Large-r grid for computation of long-ranged potentials. Default value is `missing`.
  * `n::Int`: Number of boxes for simulation. Default value is `600`.
  * `bin_size::Float64`: Size of the bin for pair correlation function and structure factor calculations. Default value is `0.05`.
  * `r_range::Float64`: Range of r values for pair correlation function calculation. Default value is `10`.
  * `k_range::Float64`: Range of k values for structure factor calculation. Default value is `10`.
  * `g2_weight_range::Float64`: Weight range for pair correlation function in the objective function. Default value is `2`.
  * `s_weight_range::Float64`: Weight range for structure factor in the objective function. Default value is `4`.
  * `n_threads::Int`: Number of threads for parallel computation. Default value is `15`.
  * `configs_per_thread::Int`: Number of configurations to generate per thread for simulation. Default value is `10`.
  * `displace::Float64`: Kick size in the metropolis Monte Carlo simulation. Default value is `0.2`.
  * `Ψ_tol::Float64`: Tolerance for convergence of the objective function. Default value is `0.005`.
  * `show_pb::Bool`: Boolean indicating whether to display a progress bar during simulation. Default value is `true`.
  * `test::Bool`: Boolean flag to indicate whether this is a test run and return a boolean indicating convergence. Default value is `false`.

## Returns

  * If `test` is true, returns `true` if convergence is achieved, `false` otherwise.
  * If `test` is false, returns the optimized potential parameters.

## Example

```
#form of the pair potential
pot(r, params) = params[1]*exp(-(r/params[2])^2)

#initial guess parameters
my_params = [1.0, 2.0] #write 1.0 instead of 1 to indicate that this is Float64

#target pair correlation function and structure factor
targ_g2(r) = 1 
targ_s(r) = 1

#optimize the parameters
InverseStatMech.optim_parametrized_pot(my_params, pot, 2, 1, targ_g2, targ_s)
```
