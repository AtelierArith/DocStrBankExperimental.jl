```
listMaxima(SITE_PATTERN_DATA)
```

# Description

Return a list of local maxima or critical points, sorted by log-likelihood. The only difference with the function `fourLeafMLE()` is that `listMaxima` does not filter out critical points which do not achieve the global optimum. See the documentation for `fourLeafMLE()`.

# Example usage:

```

random_hadamard_edge_parameters=rand(5)
test_model=computeProbabilityVector(random_hadamard_edge_parameters,1)
N=1000
SITE_PATTERN_DATA = rand(Multinomial(N,test_model))
listMaxima(SITE_PATTERN_DATA)

```
