```
set_multiplication_mode(multype)
```

Sets the algorithm used to perform matrix multiplication with interval matrices.

### Input

  * `multype` – symbol describing the algorithm used

      * `:slow` – uses traditional matrix multiplication algorithm.
      * `:rank1` – uses rank1 update
      * `:fast` – computes an enclosure of the matrix product using the midpoint-radius            notation of the matrix [[RUM10]](@ref).

### Notes

  * By default, `:fast` is used.
  * Using `fast` is generally significantly faster, but it may return larger intervals, especially if midpoint and radius have the same order of magnitude   (50% overestimate at most) [[RUM99]](@ref).
