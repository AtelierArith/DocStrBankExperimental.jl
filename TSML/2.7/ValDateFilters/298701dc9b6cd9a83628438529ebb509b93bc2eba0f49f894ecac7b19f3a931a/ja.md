```
DateValLinearImputer(
   Dict(
      :dateinterval => Dates.Hour(1),
  )
)
```

`missings`を線形補間で埋めます。

  * `:dateinterval` => グループ化に使用する時間間隔、

例:

```
Random.seed!(123)
gdate = DateTime(2014,1,1):Dates.Minute(15):DateTime(2016,1,1)
gval = Array{Union{Missing,Float64}}(rand(length(gdate)))
gmissing = 50000
gndxmissing = Random.shuffle(1:length(gdate))[1:gmissing]
X = DataFrame(Date=gdate,Value=gval)
X.Value[gndxmissing] .= missing

dnnr = DateValLinearImputer()
fit!(dnnr,X)
transform!(dnnr,X)
```

実装: `fit!`, transform!`
