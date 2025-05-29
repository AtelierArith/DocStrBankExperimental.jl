```
RobustMADS(N; search = NoSearch(), poll = LTDirectionGenerator(N),
              mesh = LogMesh(), kernel = GaussKernel(1, 1), cache = Cache(N))
```

Returns a `RobustMADS` object where `N` is the dimenionality of the problem. See Audet et al. 2018.
