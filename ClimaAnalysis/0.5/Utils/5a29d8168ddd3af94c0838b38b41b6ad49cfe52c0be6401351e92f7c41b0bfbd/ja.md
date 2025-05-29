```
split_by_season(dates::AbstractArray{<: Dates.DateTime})
```

日付を季節ごとに分割した4つのベクターを返します。

季節の月は3月から5月、6月から8月、9月から11月、12月から2月です。タプルの順序はMAM、JJA、SON、DJFです。

# 例

```jldoctest
julia> import Dates

julia> dates = [Dates.DateTime(2024, 1, 1), Dates.DateTime(2024, 3, 1), Dates.DateTime(2024, 6, 1), Dates.DateTime(2024, 9, 1)];

julia> split_by_season(dates)
([Dates.DateTime("2024-03-01T00:00:00")], [Dates.DateTime("2024-06-01T00:00:00")], [Dates.DateTime("2024-09-01T00:00:00")], [Dates.DateTime("2024-01-01T00:00:00")])
```
