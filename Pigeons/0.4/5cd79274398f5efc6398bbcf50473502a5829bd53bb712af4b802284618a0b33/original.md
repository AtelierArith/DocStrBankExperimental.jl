```julia
get_sample(pt)
get_sample(pt, chain)

```

The `chain` option can be omitted and by default the  first chain targetting the distribution of interest will be used  (in many cases, there will be only one, in variational cases, two).
