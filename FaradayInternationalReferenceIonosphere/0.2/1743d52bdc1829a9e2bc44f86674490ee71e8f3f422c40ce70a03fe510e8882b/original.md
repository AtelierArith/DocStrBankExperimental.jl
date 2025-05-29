```
FaradayInternationalReferenceIonosphere
```

`FaradayInternationalReferenceIonosphere` is a collection of convenience functions for working with Faraday-International Reference Ionosphere (FIRI) model profiles.

The underlying FIRI-2018 model `DATA`, `HEADER`, and `ALTITUDE`'s can be accessed as e.g. `FIRI.HEADER`. The unit of `ALTITUDE` is meters and `DATA` is electrons per cubic meter.

Only the function `firi` is exported, but also see `FIRI.quantile` and `FIRI.extrapolate`.

!!! tip
    For shorthand, load this package like `julia using FaradayInternationalReferenceIonosphere import FaradayInternationalReferenceIonosphere as FIRI``to reference the package as`FIRI`.


# References

Friedrich, M., Pock, C., & Torkar, K. (2018). FIRI-2018, an updated empirical model of the lower ionosphere. Journal of Geophysical Research: Space Physics, 123, 6737-6751. [doi: 10.1029/2018JA025437](https://doi.org/10.1029/2018JA025437)
