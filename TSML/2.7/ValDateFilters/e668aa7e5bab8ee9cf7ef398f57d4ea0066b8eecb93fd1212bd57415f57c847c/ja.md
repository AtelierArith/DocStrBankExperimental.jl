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

`missings`をその最近傍で埋めます。

  * `:missdirection` => 欠損データを埋める方向 (:symmetric, :reverse, :forward)
  * `:dateinterval` => グループ化に使用する時間間隔、
  * `:nnsize` => 近傍のサイズ、
  * `:strict` => 置換に厳密であるかどうかを示すブール値、
  * `:aggregator => 日付間隔に基づいて集約する関数

例:

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

実装: `fit!`, transform!`
