```
split_by_month(dates::AbstractArray{<:Dates.DateTime})
```

`dates`を月を表すベクターに分割し、時系列順に配置します。各ベクターは1つの月に対応し、ベクターの順序は季節の日付によって決まります。返り値の型は日付のベクターのベクターです。

特定の季節に対して日付が見つからない場合、そのベクターは空になります。

# 例

```jldoctest
julia> import Dates

julia> dates = vcat(collect(Dates.DateTime(2010, i) for i in 1:11), [Dates.DateTime(2011, 4)]);

julia> split_by_month(dates)
12-element Vector{Vector{Dates.DateTime}}:
 [Dates.DateTime("2010-01-01T00:00:00")]
 [Dates.DateTime("2010-02-01T00:00:00")]
 [Dates.DateTime("2010-03-01T00:00:00")]
 [Dates.DateTime("2010-04-01T00:00:00"), Dates.DateTime("2011-04-01T00:00:00")]
 [Dates.DateTime("2010-05-01T00:00:00")]
 [Dates.DateTime("2010-06-01T00:00:00")]
 [Dates.DateTime("2010-07-01T00:00:00")]
 [Dates.DateTime("2010-08-01T00:00:00")]
 [Dates.DateTime("2010-09-01T00:00:00")]
 [Dates.DateTime("2010-10-01T00:00:00")]
 [Dates.DateTime("2010-11-01T00:00:00")]
 []
```
