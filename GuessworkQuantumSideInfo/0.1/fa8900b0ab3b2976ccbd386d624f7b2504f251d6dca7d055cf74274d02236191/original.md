```
pmfN(data; tol = 1e-5) -> Vector
```

Compute the probability mass function for the number of guesses `N`, given a strategy. The `n`th entry of the output vector gives the probability for guessing the correct answer on the `n`th try, for `n = 1 : K`. If the number of allowed guesses, `K`, is smaller than `length(p)`, then there is an additional last entry which gives the probability of never guessing the correct answer.

  * `data` should be a `NamedTuple` with entries for `p`, `ρBs`, `Es`, `K`, and `povm_outcomes`
  * `tol` provides a tolerance above which to warn about imaginary or negative probabilities.
