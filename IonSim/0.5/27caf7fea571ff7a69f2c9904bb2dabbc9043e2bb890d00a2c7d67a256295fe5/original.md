```
displace(v::VibrationalMode, α::Number; method="truncated")
```

Returns the displacement operator $D(α)$ corresponding to `v`.

If `method="truncated"` (default), the matrix elements are computed according to $D(α) = exp[αa^† - α^*a]$ where $a$ and $a^†$ live in a truncated Hilbert space of dimension `modecutoff(v)+1`. Otherwise if `method="analytic"`, the matrix elements are computed assuming an infinite-dimension Hilbert space. In general, this option will not return a unitary operator.
