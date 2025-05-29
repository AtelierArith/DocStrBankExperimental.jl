```
LogarithmicAMR(α::Real,
               β::Real,
               T_max::Real = 137//10,
               MH_func = MH_from_Z,
               dMH_dZ = dMH_dZ,
               free::NTuple{2, Bool} = (true, true))
```

Subtype of [`AbstractAMR`](@ref StarFormationHistories.AbstractAMR) implementing the logarithmic age-metallicity relation where the mean metal mass fraction `Z`  at a lookback time $t_j$ (in Gyr) is `Z = α * (T_max - t_j) + β`. `α` is therefore a slope describing the rate of change in the metal mass fraction per Gyr, and `β` is the mean metal mass fraction of stars being born at a lookback time of `T_max`, which has units of Gyr. `MH_func` must be a callable (e.g., a function) that takes a single argument `Z` and converts it to [M/H]; the default function is appropriate for PARSEC stellar models. `dMH_dZ` must be a callable that takes a single argument `Z` and returns the derivative of `MH_func` with respect to `Z`. `free` controls whether `α` and `β` should be freely fit or fixed when passed into [`fit_sfh`](@ref); if `free[1] == true` then `α` will be freely fit, whereas it will fixed if `free[1] == false`. `free[2]` has the same effect but for `β`. 
