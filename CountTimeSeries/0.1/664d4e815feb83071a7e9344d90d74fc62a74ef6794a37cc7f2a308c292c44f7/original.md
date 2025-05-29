```
QPois(results)
```

Add-on function for Quasi Poisson estimation of INGARCH models.

  * `results`: Estimation results (only INGARCH)

# Example

```julia-repl
QPois(results)
```

The function uses estimation results of an INGARCH fit with Poisson distribution and estimates the overdispersion parameter according to [Christou and Fokianos (2013)](https://doi.org/10.1111/jtsa.12050). The function puts out a changed version of the input including an estimate of the overdispersion parameter. The distribution is thereby changed to "NegativeBinomial".
