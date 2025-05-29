# compare

Compare waic and psis values for models.

```julia
compare(m, ; mnames)

```

### Required arguments

```julia
* `models`                             : Vector of logprob matrices
* `criterium`                          : Either ::Val{:waic} or ::Val{:psis}
```

### Optional argument

```julia
* `mnames::Vector{Symbol}`             : Vector of model names
```

### Return values

```julia
* `df`                                 : DataFrame with statistics
```
