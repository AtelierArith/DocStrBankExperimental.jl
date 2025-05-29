```
ScaledSobolIterator(lowerbounds, upperbounds, N;
                    seq = SobolSeq(length(lowerbounds)))
```

Returns an iterator over `N` elements of a Sobol sequence between `lowerbounds` and `upperbounds`. The first `N` elements of the Sobol sequence are skipped for better uniformity (see https://github.com/stevengj/Sobol.jl)
