```
SuptBand <: PlugInConfidenceBand
```

Plug-in sup-t confidence band. Implementation follows Montiel Olea and Plagborg-Møller (2019) Algorithm 1 and may allow generalized error rate control.

Critical values computed for `SuptBand` are based on random draws from a normal distribution. Since the random numbers are drawn only once and stored in an unexported global object `_globalrandnpool`, results from the same Julia session remain unchanged if executed multiple times. However, results obtained across different sessions are not identical because the random numbers generated vary. See Julia manual section on [`Random`](https://docs.julialang.org/en/v1/stdlib/Random/) for reproducibility of random numbers.

# References

  * Montiel Olea, José Luis and Mikkel Plagborg-Møller. 2019. "Simultaneous Confidence Bands: Theory, Implementation, and an Application to SVARs." Journal of Applied Econometrics 34 (1): 1-17.
