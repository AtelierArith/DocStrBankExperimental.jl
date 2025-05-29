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

`missings`をその最寄りの隣接点で埋めます。最初の列がDateクラスで、他の列がUnion{Missings,Real}であると仮定します。DateValNNerとDateValizer+Imputeを使用して、日付列と連結された各数値列を処理します。

  * `:type` => 補完のタイプ（線形補間または最近傍）
  * `:missdirection` => 欠損データを埋める方向（:symmetric, :reverse, :forward）
  * `:dateinterval` => グループ化に使用する時間間隔、
  * `:nnsize` => 隣接点のサイズ、
  * `:strict` => 置換に厳密であるかどうかを示すブール値、
  * `:aggregator => 日付間隔に基づいて集約する関数

例:

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

実装: `fit!`, transform!`
