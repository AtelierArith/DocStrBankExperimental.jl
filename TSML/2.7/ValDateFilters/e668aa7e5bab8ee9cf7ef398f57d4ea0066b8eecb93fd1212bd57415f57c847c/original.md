```
DateValNNer(
   Dict(
      :missdirection => :symmetric, #:reverse, # or :forward or :symmetric
      :dateinterval => Dates.Hour(1),
      :nnsize => 1,
      :strict => false,
      :aggregator => :median
  )
)
```

Fills `missings` with their nearest-neighbors.

  * `:missdirection` => direction to fill missing data (:symmetric, :reverse, :forward)
  * `:dateinterval` => time period to use for grouping,
  * `:nnsize` => neighborhood size,
  * `:strict` => boolean value to indicate whether to be strict about replacement or not,
  * `:aggregator => function to aggregate based on date interval

Example:

```
Random.seed!(123)
gdate = DateTime(2014,1,1):Dates.Minute(15):DateTime(2016,1,1)
gval = Array{Union{Missing,Float64}}(rand(length(gdate)))
gmissing = 50000
gndxmissing = Random.shuffle(1:length(gdate))[1:gmissing]
X = DataFrame(Date=gdate,Value=gval)
X.Value[gndxmissing] .= missing

dnnr = DateValNNer(Dict(
      :dateinterval=>Dates.Hour(1),
      :nnsize=>10,
      :missdirection => :symmetric,
      :strict=>true,
      :aggregator => :mean))
fit!(dnnr,X)
transform!(dnnr,X)
```

Implements: `fit!`, transform!`
