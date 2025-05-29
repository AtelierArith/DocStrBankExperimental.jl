```
ABC(;
    N = 50,
    Ne = div(N+1, 2),
    No = div(N+1, 2),
    limit=10,
    information = Information(),
    options = Options()
)
```

ABC implements the original parameters for the Artificial Bee Colony Algorithm. `N` is the population size, `Ne` is the number of employees, `No` is the number of outlookers bees. `limit` is related to the times that a solution is visited.

# Example

```jldoctest
julia> f(x) = sum(x.^2)
f (generic function with 1 method)

julia> optimize(f, [-1 -1 -1; 1 1 1.0], ABC())
+=========== RESULT ==========+
  iteration: 595
    minimum: 4.03152e-28
  minimizer: [1.489845115451046e-14, 1.2207275971717747e-14, -5.671872444705246e-15]
    f calls: 30020
 total time: 0.0360 s
+============================+

julia> optimize(f, [-1 -1 -1; 1 1 1.0], ABC(N = 80,  No = 20, Ne = 50, limit=5))
+=========== RESULT ==========+
  iteration: 407
    minimum: 8.94719e-08
  minimizer: [8.257485723496422e-5, 0.0002852795196258074, -3.5620824723352315e-5]
    f calls: 30039
 total time: 0.0432 s
+============================+
```
