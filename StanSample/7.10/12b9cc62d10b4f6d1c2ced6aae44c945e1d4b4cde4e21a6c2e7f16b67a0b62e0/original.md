Create a `name`_summary.csv file. 

```julia
stan_summary(m)
stan_summary(m, printsummary)

```

# Extended help

### Required arguments

```julia
* `model::SampleModel             : SampleModel
```

### Optional positional arguments

```julia
* `printsummary=false             : Display summary
```

After completion a ...*summary.csv file has been created. This file can be read as a DataFrame in by `df = read*summary(model))`
