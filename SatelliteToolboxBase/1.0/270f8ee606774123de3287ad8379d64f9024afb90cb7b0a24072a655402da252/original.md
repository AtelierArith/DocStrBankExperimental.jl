```
eccentric_to_mean_anomaly(e::T1, E::T2) where {T1, T2} -> T
```

Compute the mean anomaly (0, 2π) [rad] given the orbit eccentricity `e` and the eccentric anomaly `E` [rad].

!!! note
    The output type `T` is obtained by promoting `T1` and `T2` to float.

