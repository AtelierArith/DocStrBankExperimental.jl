```
CountMap(T::Type)
CountMap(dict::AbstractDict{T, Int})
```

ユニークな値をその出現回数にマッピングする辞書を追跡します。 `StatsBase.countmap` に似ています。

カウントは、`fit!(::CountMap{T}, ::Pair{T,Int})` メソッドを使用して、1以外の値で増加（および減少）させることができます。例えば：

```julia
o = fit!(CountMap(String), ["A", "B"])
fit!(o, "A" => 5)
fit!(o, "A" => -1)
```

# 例

```
o = fit!(CountMap(Int), rand(1:10, 1000))
value(o)
OnlineStatsBase.probs(o)
OnlineStats.pdf(o, 1)
collect(keys(o))
sort!(o)
delete!(o, 1)
```
