```
WOA(;N = 30, information = Information(), options = Options())
```

Parameters for the Whale Optimization Algorithm. `N` is the population size (number of whales).

# Example

```jldoctest
julia> f(x) = sum(x.^2)
f (generic function with 1 method)

julia> optimize(f, [-1 -1 -1; 1 1 1.0], WOA())
+=========== RESULT ==========+
  iteration: 500
    minimum: 3.9154600000000003e-100
  minimizer: [8.96670478694908e-52, -1.9291317455298046e-50, 4.3113080446722046e-51]
    f calls: 15000
 total time: 0.0134 s
+============================+

julia> optimize(f, [-1 -1 -1; 1 1 1.0], WOA(N = 100))
+=========== RESULT ==========+
  iteration: 500
    minimum: 1.41908e-145
  minimizer: [9.236161414012512e-74, -3.634919950380001e-73, 3.536831799149254e-74]
    f calls: 50000
 total time: 0.0588 s
+============================+

```
