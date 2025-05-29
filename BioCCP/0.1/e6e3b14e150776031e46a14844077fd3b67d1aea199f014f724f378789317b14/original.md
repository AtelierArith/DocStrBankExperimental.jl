```
expectation_minsamplesize(n; p=ones(n)/n, m=1, r=1, normalize=true)
```

Calculates the expected minimum number of designs  `E[T]` to observe each module at least `m` times.

  * `n`: number of modules in the design space
  * `p`: vector with the probabilities or abundances of the different modules
  * `m`: number of times each module has to be observed in the sampled set of designs
  * `r`: number of modules per design
  * normalize: if true, normalize `p`

References:

  * Doumas, A. V., & Papanicolaou, V. G. (2016). The coupon collector’s problem revisited:   generalizing the double Dixie cup problem of Newman and Shepp. ESAIM: Probability   and Statistics, 20, 367-399.
  * Boneh, A., & Hofri, M. (1997). The coupon-collector problem revisited—a survey of   engineering problems and computational methods. Stochastic Models, 13(1), 39-66.

## Examples

```julia-repl
julia> n = 100
julia> expectation_minsamplesize(n; p=ones(n)/n, m=1, r=1, normalize=true)
518
```
