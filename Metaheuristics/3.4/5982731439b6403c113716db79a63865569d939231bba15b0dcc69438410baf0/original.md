```
ECA(;
    η_max = 2.0,
    K = 7,
    N = 0,
    N_init = N,
    p_exploit = 0.95,
    p_bin = 0.02,
    p_cr = Float64[],
    adaptive = false,
    resize_population = false,
    information = Information(),
    options = Options()
)
```

Parameters for the metaheuristic ECA: step-size `η_max`,`K` is number of vectors to generate the center of mass, `N` is the population size.

# Example

```jldoctest
julia> f(x) = sum(x.^2)
f (generic function with 1 method)

julia> optimize(f, [-1 -1 -1; 1 1 1.0], ECA())
+=========== RESULT ==========+
  iteration: 1429
    minimum: 3.3152400000000004e-223
  minimizer: [4.213750597785841e-113, 5.290977430907081e-112, 2.231685329262638e-112]
    f calls: 29989
 total time: 0.1672 s
+============================+

julia> optimize(f, [-1 -1 -1; 1 1 1.0], ECA(N = 10, η_max = 1.0, K = 3))
+=========== RESULT ==========+
  iteration: 3000
    minimum: 0.000571319
  minimizer: [-0.00017150889316537758, -0.007955828028420616, 0.022538733289139145]
    f calls: 30000
 total time: 0.1334 s
+============================+
```
