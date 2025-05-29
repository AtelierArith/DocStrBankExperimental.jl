```
split_by_season_across_time(dates::AbstractArray{<:Dates.DateTime})
```

`dates`を季節を表すベクトルに分割し、時系列順に配置します。各ベクトルは単一の季節に対応し、ベクトルの順序は季節の日付によって決まります。返り値の型は日付のベクトルのベクトルです。

特定の季節に対して日付が見つからない場合、そのベクトルは空になります。最初のベクトルは空でないことが保証されています。

この関数は`split_by_season`とは異なり、`split_by_season`は日付を異なる季節に分割し、日付が異なる年の季節から来る可能性を無視します。それに対して、`split_by_season_across_time`は各年の季節に日付を分割します。

# 例

```jldoctest
julia> import Dates

julia> dates = collect(Dates.DateTime(2010, i) for i in 1:12);

julia> split_by_season_across_time(dates)
5-element Vector{Vector{Dates.DateTime}}:
 [Dates.DateTime("2010-01-01T00:00:00"), Dates.DateTime("2010-02-01T00:00:00")]
 [Dates.DateTime("2010-03-01T00:00:00"), Dates.DateTime("2010-04-01T00:00:00"), Dates.DateTime("2010-05-01T00:00:00")]
 [Dates.DateTime("2010-06-01T00:00:00"), Dates.DateTime("2010-07-01T00:00:00"), Dates.DateTime("2010-08-01T00:00:00")]
 [Dates.DateTime("2010-09-01T00:00:00"), Dates.DateTime("2010-10-01T00:00:00"), Dates.DateTime("2010-11-01T00:00:00")]
 [Dates.DateTime("2010-12-01T00:00:00")]
```
