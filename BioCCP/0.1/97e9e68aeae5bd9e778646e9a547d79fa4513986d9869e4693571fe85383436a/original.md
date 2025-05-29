```
expectation_fraction_collected(n::Integer, t::Integer; p=ones(n)/n, r=1, normalize=true)
```

Calculates the fraction of all modules that is expected to be observed after collecting `t` designs.

  * `n`: number of modules in design space
  * `t`: sample size/number of designs
  * `p`: vector with the probabilities or abundances of the different modules
  * `r`: number of modules per design
  * normalize: if true, normalize `p`

References:

  * Boneh, A., & Hofri, M. (1997). The coupon-collector problem revisited—a survey of engineering problems and computational methods. Stochastic Models, 13(1), 39-66.

## Examples

```julia-repl
julia> n = 100
julia> t = 200
julia> expectation_fraction_collected(n, t; p=ones(n)/n, r=1, normalize=true)
0.8660203251420364
```
