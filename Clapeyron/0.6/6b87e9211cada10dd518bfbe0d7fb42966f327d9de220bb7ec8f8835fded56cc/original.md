```
MichelsenTPFlash{T}(;kwargs...)
```

Method to solve non-reactive multicomponent flash problem by Michelsen's method.

Only two phases are supported. if `K0` is `nothing`, it will be calculated via the Wilson correlation.

### Keyword Arguments:

  * `equilibrium`: `:vle` for liquid vapor equilibria, `:lle` for liquid liquid equilibria, `:unknown` if not specified
  * `K0`: initial guess for the constants K
  * `x0`: initial guess for the composition of phase x
  * `y0`: initial guess for the composition of phase y
  * `vol0`: initial guesses for phase x and phase y volumes
  * `K_tol`: tolerance to stop the calculation
  * `ss_iters`: number of Successive Substitution iterations to perform
  * `nacc`: accelerate successive substitution method every nacc steps. Should be a integer bigger than 3. Set to 0 for no acceleration.
  * `second_order`: wheter to solve the gibbs energy minimization using the analytical hessian or not
  * `noncondensables`: arrays with names (strings) of components non allowed on the liquid phase. In the case of LLE equilibria, corresponds to the `x` phase
  * `nonvolatiles`: arrays with names (strings) of components non allowed on the vapour phase. In the case of LLE equilibria, corresponds to the `y` phase
  * `flash_result::FlashResult`: can be provided instead of `x0`,`y0` and `vol0` for initial guesses
