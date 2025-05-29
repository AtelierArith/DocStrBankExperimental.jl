```
LinearAMR(α::Real,
          β::Real,
          T_max::Real = 137//10,
          free::NTuple{2, Bool} = (true, true))
```

Subtype of [`AbstractAMR`](@ref StarFormationHistories.AbstractAMR) implementing the linear age-metallicity relation where the mean metallicity at a lookback time $t_j$ (in Gyr) is `μ_j = α * (T_max - t_j) + β`. `α` is therefore a slope describing the rate of change in the metallicity per Gyr, and `β` is the mean metallicity value of stars being born at a lookback time of `T_max`, which has units of Gyr. `free` controls whether `α` and `β` should be freely fit or fixed when passed into [`fit_sfh`](@ref); if `free[1] == true` then `α` will be freely fit, whereas it will fixed if `free[1] == false`. `free[2]` has the same effect but for `β`. 
