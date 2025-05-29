```
DateValizer(
   Dict(
    :medians => DataFrame(),
    :dateinterval => Dates.Hour(1)
  )
)
```

Normalizes and cleans time series by replacing `missings` with global medians  computed based on time period groupings.

Example:

```
# generate random values with missing data
Random.seed!(123)
gdate = DateTime(2014,1,1):Dates.Minute(15):DateTime(2016,1,1)
gval = Array{Union{Missing,Float64}}(rand(length(gdate)))
gmissing = 50000
gndxmissing = Random.shuffle(1:length(gdate))[1:gmissing]
X = DataFrame(Date=gdate,Value=gval)
X.Value[gndxmissing] .= missing

dvzr = DateValizer(Dict(:dateinterval=>Dates.Hour(1)))
fit!(dvzr,X)
transform!(dvzr,X)
```

Implements: `fit!`, `transform!`
