```
skeletonize(R) → R_skel
```

Skeletonize the `RecurrenceMatrix R` by using the algorithm proposed by Kraemer & Marwan [^Kraemer2019]. This function returns `R_skel`, a recurrence matrix, which only consists of diagonal lines of "thickness" one.

[^Kraemer2019]: Kraemer, K.H., Marwan, N. (2019). [Border effect corrections for diagonal line based recurrence quantification analysis measures. Physics Letters A 383(34)](https://doi.org/10.1016/j.physleta.2019.125977).
