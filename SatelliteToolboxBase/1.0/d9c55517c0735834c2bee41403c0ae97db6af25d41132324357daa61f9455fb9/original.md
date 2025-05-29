```
true_to_eccentric_anomaly(e::T1, f::T2) where {T1, T2} -> T
```

Compute the eccentric anomaly (0, 2π) [rad] given the orbit eccentricity `e` and the true anomaly `f` [rad].

!!! note
    The output type `T` is obtained by promoting `T1` and `T2` to float.

