```
DateValMultiNNer(
   Dict(
      :type => :knn # :linear
      :missdirection => :symmetric, #:reverse, # or :forward or :symmetric
      :dateinterval => Dates.Hour(1),
      :nnsize => 1,
      :strict => false,
      :aggregator => :median
  )
)
```

Fills `missings` with their nearest-neighbors. It assumes that first column is a Date class and the other columns are Union{Missings,Real}. It uses DateValNNer and DateValizer+Impute to process each numeric column concatendate with the Date column.

  * `:type` => type of imputation which can be a linear interpolation or nearest neighbor
  * `:missdirection` => direction to fill missing data (:symmetric, :reverse, :forward)
  * `:dateinterval` => time period to use for grouping,
  * `:nnsize` => neighborhood size,
  * `:strict` => boolean value to indicate whether to be strict about replacement or not,
  * `:aggregator => function to aggregate based on date interval

Example:

```
Random.seed!(123)
gdate = DateTime(2014,1,1):Dates.Minute(15):DateTime(2016,1,1)
gval1 = Array{Union{Missing,Float64}}(rand(length(gdate)))
gval2 = Array{Union{Missing,Float64}}(rand(length(gdate)))
gval3 = Array{Union{Missing,Float64}}(rand(length(gdate)))
gmissing = 50000
gndxmissing1 = Random.shuffle(1:length(gdate))[1:gmissing]
gndxmissing2 = Random.shuffle(1:length(gdate))[1:gmissing]
gndxmissing3 = Random.shuffle(1:length(gdate))[1:gmissing]
X = DataFrame(Date=gdate,Temperature=gval1,Humidity=gval2,Ozone=gval3)
X.Temperature[gndxmissing1] .= missing
X.Humidity[gndxmissing2] .= missing
X.Ozone[gndxmissing3] .= missing

dnnr = DateValMultiNNer(Dict(
      :type=>:linear,
      :dateinterval=>Dates.Hour(1),
      :nnsize=>10,
      :missdirection => :symmetric,
      :strict=>false,
      :aggregator => :mean))
fit!(dnnr,X)
transform!(dnnr,X)
```

Implements: `fit!`, transform!`
