Read summary output file created by stansummary. 

```julia
read_summary(m)
read_summary(m, printsummary)

```

# Extended help

### Required arguments

```julia
* `m`                                  : A Stan model object, e.g. SampleModel
```

### Optional positional arguments

```julia
* `printsummary=false`                 : Print cmdstan summary
```

### Returns

```julia
* `df`                                 : Dataframe containing the cmdstan summary
```
