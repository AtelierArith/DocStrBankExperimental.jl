```
Sample(size, [weights]; replace=true, ordered=false, rng=default_rng())
```

Sample `size` rows of table using `weights` with or without replacement depending on the option `replace`. The option `ordered` can be used to return samples in the same order of the original table.

# Examples

```julia
Sample(1000)
Sample(1000, replace=false)
Sample(1000, replace=false, ordered=true)

# with rng
using Random
rng = MersenneTwister(2)
Sample(1000, rng=rng)

# with weights
Sample(10, rand(100))
```
