```
dmedian(dInfo::Dinfo, columns::Vector{Int})
```

Compute a median in a distributed fashion, avoiding data transfer and memory capacity that is required to compute the median in the classical way by sorting. All data must be finite and defined. If the median is just between 2 values, the lower one is chosen.

The algorithm is approximative, searching for a good median by halving interval and counting how many values are below the threshold. `iters` can be increased to improve precision, each value adds roughly 1 bit to the precision. The default value is 20, which corresponds to precision 10e-6 times the data range.
