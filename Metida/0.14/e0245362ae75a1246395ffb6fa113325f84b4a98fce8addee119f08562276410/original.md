```
bootstrap(lmm::LMM; double = false, n = 100, verbose = true, init = lmm.result.theta, rng = default_rng())
```

Parametric bootstrap.

!!! warning
    Experimental: API not stable


  * double - use double approach (default - false);
  * n - number of bootstrap samples;
  * verbose - show progress bar;
  * init - initial values for lmm;
  * rng - random number generator.

Parametric bootstrap based on generating random responce vector from known distribution, that given from fitted LMM model.

  * Simple bootstrap:

For one-stage bootstrap variance parameters and coefficients simulated in one step.  

  * Double bootstrap:

For double bootstrap (two-tage) variance parameters simulated in first cycle, than they used for simulating coefficients and var(β) on stage two.  On second stage parent-model β used for simulations. 

```julia
lmm = Metida.LMM(@formula(var~sequence+period+formulation), df0m;
random = Metida.VarEffect(Metida.@covstr(formulation|subject), Metida.CSH),
)
Metida.fit!(lmm)
bt = Metida.bootstrap(lmm; n = 1000, double = true, rng = MersenneTwister(1234))
confint(bt)
```

See also: [`confint`](@ref), [`Metida.miboot`](@ref), [`Metida.nvar`](@ref), [`Metida.tvar`](@ref),  [`Metida.straps`](@ref), [`Metida.sdstraps`](@ref), [`Metida.thetastraps`](@ref)
