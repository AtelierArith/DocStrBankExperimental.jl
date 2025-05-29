```julia
AB3(; thread = OrdinaryDiffEq.False())
```

Adams-Bashforth Explicit Method The 3-step third order multistep method.         Ralston's Second Order Method is used to calculate starting values.

### Keyword Arguments

  * `thread`: determines whether internal broadcasting on appropriate CPU arrays should be serial (`thread = OrdinaryDiffEq.False()`) or use multiple threads (`thread = OrdinaryDiffEq.True()`) when Julia is started with multiple threads.

## References

E. Hairer, S. P. Norsett, G. Wanner, Solving Ordinary Differential Equations I, Nonstiff Problems. Computational Mathematics (2nd revised ed.), Springer (1996) doi: https://doi.org/10.1007/978-3-540-78862-1
