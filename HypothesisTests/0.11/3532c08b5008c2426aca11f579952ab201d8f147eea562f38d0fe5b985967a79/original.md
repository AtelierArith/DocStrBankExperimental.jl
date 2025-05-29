```
ApproximatePermutationTest([rng::AbstractRNG,] x::Vector, y::Vector, f::Function, n::Int)
```

Perform a permutation test (a.k.a. randomization test) of the null hypothesis that `f(x)` is equal to `f(y)`.  `n` of the `factorial(length(x)+length(y))` permutations are sampled at random. A random number generator can optionally be passed as the first argument. The default generator is `Random.default_rng()`.
