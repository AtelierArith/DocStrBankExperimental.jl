```
KeyRateZero(timepoint,shift=0.001) <: KeyRateDuration
```

Shift the par curve by the given amount at the given timepoint. Use in conjunction with `duration` to calculate the key rate duration.

Unlike other duration statistics which are computed using analytic derivatives, `KeyRateDuration` is computed via a shift-and-compute the yield curve approach.

`KeyRateZero` is less commonly reported (than [`KeyRatePar`](@ref)) in the fixed income markets, even though the latter has more analytically attractive properties. See the discussion of KeyRateDuration in the FinanceModels.jl docs.
