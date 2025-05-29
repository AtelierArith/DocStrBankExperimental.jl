```
neg_binom(r::Real, p::Real)
```

Sample an `Int` from a Negative Binomial distribution. Returns the number of failures before the `r`th success in a sequence of independent Bernoulli trials. `r` is the number of successes (which may be fractional) and `p` is the probability of success per trial.
