```
generate_effQTL!(gmap::QMSimMap, af::QMSimAlleleFrequency, dist_or_func, args...; expvar=1.0)
```

Generate and adjust QTL effects given allele frequency `af` and update the map `gmap`. A distribution `dist` (defined in the `Distribution` package) or a function `func` shoud be provided to generate QTL effects optionally accompanied with arguments `args...`. The generated effects will be scaled so that the expected genetic variance equals to `expvar`. The function supports a map file with multiple traits.
