```
evaluate(O, JarrowRudd(), risk_neutral = true, N = 1000)
```

Evaluate option `O` using `JarrowRudd` binomial model (defaults to the risk-neutral version).

# Arguments

  * `O::Option`: option
  * `risk_neutral`: `true` if risk neutral, `false` if equal probability.
  * `N`: number of paths to simulate
