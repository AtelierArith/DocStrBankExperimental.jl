```
distancetrace_spaceneeded(n, p; bits=64) = Base.format_bytes(binomial(n,2) * p * bits)
```

how much memory is needed to store spectral residual trace

Args:

  * n: number of samples
  * p: number of partitions/components
