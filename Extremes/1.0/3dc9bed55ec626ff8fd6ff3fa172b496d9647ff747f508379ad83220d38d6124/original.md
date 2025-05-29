```
gumbelfitpwm(df::DataFrame, datacol::Symbol)::pwmAbstractExtremeValueModel
```

Estimate the Gumbel parameters with the probability weighted moments.

Block maxima data are in the column `datacol` of the dataframe `df`.
