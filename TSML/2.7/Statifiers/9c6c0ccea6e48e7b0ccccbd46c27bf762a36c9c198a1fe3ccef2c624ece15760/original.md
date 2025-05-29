```
Statifier(Dict(
   :processmissing => true
))
```

Outputs summary statistics such as mean, median, quartile, entropy, kurtosis, skewness, etc. with parameter: 

  * `:processmissing` => `boolean` to indicate whether to include `missing` data stats.

Example:

```
dt=[missing;rand(1:10,3);missing;missing;missing;rand(1:5,3)]
dat = DataFrame(Date= DateTime(2017,12,31,1):Dates.Hour(1):DateTime(2017,12,31,10) |> collect,
                Value = dt)

statfier = Statifier(Dict(:processmissing=>false))

fit!(statfier,dat)
results=transform!(statfier,dat)
```

Implements: `fit!`, `transform!`
