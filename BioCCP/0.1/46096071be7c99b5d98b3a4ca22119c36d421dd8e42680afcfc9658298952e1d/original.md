```
success_probability(n::Integer, t::Integer; p=ones(n)/n, m::Integer=1, r=1, normalize=true)
```

Calculates the success probability `F(t) = P(T ≤ t)` or the probability that  the minimum number of designs `T` to see each module at least `m` times is smaller than `t`.

  * `n`: number of modules in design space
  * `t`: sample size/number of designs for which to calculate the success probability
  * `p`: vector with the probabilities or abundances of the different modules
  * `m`: number of complete sets of modules that need to be collected
  * `r`: number of modules per design
  * normalize: if true, normalize `p`

References:

  * Boneh, A., & Hofri, M. (1997). The coupon-collector problem revisited—a survey of engineering problems and computational methods. Stochastic Models, 13(1), 39-66.

## Examples

```julia-repl
julia> n = 100
julia> t = 600
julia> success_probability(n, t; p=ones(n)/n, m=1, r=1, normalize=true)
0.7802171997092149
```
