```
DateValizer(
   Dict(
    :medians => DataFrame(),
    :dateinterval => Dates.Hour(1)
  )
)
```

時間系列を正規化し、クリーンアップします。`missings`を時間期間のグループに基づいて計算されたグローバル中央値で置き換えます。

例:

```
# 欠損データを含むランダム値を生成
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

実装: `fit!`, `transform!`
