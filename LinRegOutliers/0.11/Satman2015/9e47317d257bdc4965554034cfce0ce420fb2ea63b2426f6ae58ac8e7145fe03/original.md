```
dominates(p1::Array, p2::Array)
```

Return true if each element in p1 is not less than the corresponding element in p2 and at least one element in p1 is bigger than the corresponding element in p2.

# Arguments

  * `p1::Array`: Numeric array of n elements.
  * `p2::Array`: Numeric array of n elements.

# Examples

```julia-repl
julia> dominates([1,2,3], [1,2,1])
true

julia> dominates([0,0,0,0], [1,0,0,0])
false
```

# References

Satman, Mehmet Hakan. "A new algorithm for detecting outliers in linear regression."  International Journal of statistics and Probability 2.3 (2013): 101.

Deb, Kalyanmoy, et al. "A fast elitist non-dominated sorting genetic algorithm for multi-objective optimization: NSGA-II."  International conference on parallel problem solving from nature. Springer, Berlin, Heidelberg, 2000.
