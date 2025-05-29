```
Normalizer(Dict(
   :method => :zscore
))
```

連続的な特徴をzスコア、ユニットレンジ、平方根、対数、pca、ppcaのような正規化された形式に変換します。パラメータは次のとおりです：

  * `:method` => `:zscore` または `:unitrange` または `:sqrt` または `:log` または `pca` または `ppca` または `fa`
  * `:zscore` => 中心化とスケーリングを伴う標準zスコア
  * `:unitrange` => 中心化とスケーリングを伴うユニットレンジ正規化
  * `:sqrt` => 平方根変換
  * `:pca` => 主成分分析変換
  * `:ppca` => 確率的pca
  * `:fa` => 因子分析
  * `:log` => 対数変換

例：

```
function generatedf()
    Random.seed!(123)
    gdate = DateTime(2014,1,1):Dates.Minute(15):DateTime(2016,1,1)
    gval1 = rand(length(gdate))
    gval2 = rand(length(gdate))
    gval3 = rand(length(gdate))
    X = DataFrame(Date=gdate,Value1=gval1,Value2=gval2,Value3=gval3)
    X
end

X = generatedf()
norm = Normalizer(Dict(:method => :zscore))
fit!(norm,X)
res=transform!(norm,X)
```

実装：`fit!`、`transform!`
