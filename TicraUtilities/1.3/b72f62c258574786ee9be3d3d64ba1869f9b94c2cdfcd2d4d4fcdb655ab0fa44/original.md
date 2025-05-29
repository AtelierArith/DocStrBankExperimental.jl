```
get_qsmns(s::SPHQPartition)
```

Return the offset array `qsmns::OffsetArray{ComplexF64, 3}` that contains the  Q coefficients, assuming exp(jωt) time variation and using the Ticra normalization  convention.  The array has axes `(1:2, -mmax:mmax, 1:nmax)`, meaning  that some of  the entries (those with `n < abs(m)`) are always zero.
