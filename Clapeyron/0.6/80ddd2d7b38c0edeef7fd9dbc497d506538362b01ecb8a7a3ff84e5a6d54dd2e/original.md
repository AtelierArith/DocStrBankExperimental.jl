```
MultiPhaseTPFlash(;kwargs...)
```

Method to solve non-reactive multiphase (`np` phases), multicomponent (`nc` components) flash problem.

The flash algorithm uses successive stability tests to find new phases [1], and then tries to solve the system via rachford-rice and succesive substitution for `nc * np * ss_iters` iterations.

If the Rachford-Rice SS fails to converge, it proceeds to solve the system via gibbs minimization in VT-space using lnK-β-ρ as variables [3].

The algorithm finishes when SS or the gibbs minimization converges and all resulting phases are stable.

If the result of the phase equilibria is not stable, then it proceeds to add/remove phases again, for a maximum of `phase_iters` iterations.

### Keyword Arguments:

  * `K0` (optional), initial guess for the constants K
  * `x0` (optional), initial guess for the composition of phase x
  * `y0` (optional), initial guess for the composition of phase y
  * `n0` (optional), initial guess for all compositions. it can be a matrix or a vector of vectors.
  * `K_tol = sqrt(eps(Float64))`, tolerance to stop the calculation (`norm(lnK,1) < K_tol`)
  * `ss_iters = 4`, number of Successive Substitution iterations to perform
  * `nacc = 3`, accelerate successive substitution method every nacc steps. Should be a integer bigger than 3. Set to 0 for no acceleration.
  * `second_order = true`, whether to solve the gibbs energy minimization using the analytical hessian or not. If set to `false`, the gibbs minimization will be done using L-BFGS.
  * `full_tpd` = false, whether to start with a simple K-split or using an intensive TPD search first.
  * `max_phases = typemax(Int)`, the algorithm stops if there are more than `min(max_phases,nc)` phases
  * `phase_iters = 20`, the maximum number of solve-add/remove-phase iterations

## References

1. Thermopack - Thermodynamic equilibrium algorithms reimplemented in a new framework. (2020, September 08). https://github.com/thermotools/thermopack. Retrieved May 4, 2024, from https://github.com/thermotools/thermopack/blob/main/docs/memo/flash/flash.pdf
2. Okuno, R., Johns, R. T. T., & Sepehrnoori, K. (2010). A new algorithm for Rachford-Rice for multiphase compositional simulation. SPE Journal, 15(02), 313–325. [doi:10.2118/117752-pa](https://doi.org/10.2118/117752-pa)
3. Adhithya, T. B., & Venkatarathnam, G. (2021). New pressure and density based methods for isothermal-isobaric flash calculations. Fluid Phase Equilibria, 537(112980), 112980. [doi:10.1016/j.fluid.2021.112980](https://doi.org/10.1016/j.fluid.2021.112980)
