```
XPRS_INVERTFREQ
```

Simplex: The frequency with which the basis will be inverted. (integer)

The basis is maintained in a factorized form and on most simplex iterations it is incrementally updated to reflect the step just taken. This is considerably faster than computing the full inverted matrix at each iteration, although after a number of iterations the basis becomes less well-conditioned and it becomes necessary to compute the full inverted matrix. The value of `INVERTFREQ` specifies the maximum number of iterations between full inversions.

Default value: `-1` the frequency is determined automatically.

Domain: -1,0~+INF
