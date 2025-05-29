```
autoprior(mean, stddev; lower=-Inf, upper=Inf)
```

Helper function that automatically constructs a prior distribution with the given mean, standard deviation, and support. Note that `lower < mean <= upper` must be satisfied. For unbounded variables, `Normal` is returned. For variabels bounded from below (i.e. either lower or upper bound is finite), a transformed `LogNormal` distribution is constructed. For double bounded variables, (i.e. both lower and upper are finite) a tranformed `Beta` distribution is constructed.
