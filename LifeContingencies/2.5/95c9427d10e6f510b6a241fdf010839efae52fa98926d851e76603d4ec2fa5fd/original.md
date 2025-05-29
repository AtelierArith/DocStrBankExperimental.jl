```
omega(lc::LifeContingency)
omega(l::Life)
omega(i::InterestRate)
```

# `Life`s and `LifeContingency`s

Returns the last defined time*period for both the interest rate and mortality table. Note that this is *different* than calling `omega` on a `MortalityTable`, which will give you the last `attained*age`.

Example: if the `LifeContingency` has issue age 60, and the last defined attained age for the `MortalityTable` is 100, then `omega` of the `MortalityTable` will be `100` and `omega` of the  `LifeContingency` will be `40`.

# `InterestRate`s

The last period that the interest rate is defined for. Assumed to be infinite (`Inf`) for      functional and constant interest rate types. Returns the `lastindex` of the vector if      a vector type.
