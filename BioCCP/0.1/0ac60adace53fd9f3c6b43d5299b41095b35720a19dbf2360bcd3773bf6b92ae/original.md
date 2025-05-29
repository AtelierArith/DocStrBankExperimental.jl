```
std_minsamplesize(n::Integer; p=ones(n)/n, m::Integer=1, r=1, normalize=true)
```

Calculates the standard deviation on the minimum number of designs to observe each module at least `m` times.

  * `n`: number of modules in the design space
  * `p`: vector with the probabilities or abundances of the different modules
  * `m`: number of complete sets of modules that need to be collected
  * `r`: number of modules per design
  * normalize: if true, normalize `p`

## Examples

```julia-repl
julia> n = 100
julia> std_minsamplesize(n; p=ones(n)/n, m=1, r=1, normalize=true)
126
```
