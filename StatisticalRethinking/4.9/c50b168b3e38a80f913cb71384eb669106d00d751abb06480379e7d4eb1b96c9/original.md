# quap

Quadratic approximation of a posterior distribution in a DataFrame

### Method

```julia
quap(df) 
```

### Required arguments

```julia
* `df::DataFrame`                      : Dataframe generated from samples (chains)
```

### Return values

```julia
* `result::NamedTuple`                 : NamedTuple representing the quadratic approximation
```

To convert to a Dict use:

```julia
dct = Dict(pairs(result))
```

### Example

```julia
# Run stan_sample() on a SampleModel
if success(rc)
  
  df = read_samples(sm; output_format=:dataframe)
  q = quap(df)
end
```
