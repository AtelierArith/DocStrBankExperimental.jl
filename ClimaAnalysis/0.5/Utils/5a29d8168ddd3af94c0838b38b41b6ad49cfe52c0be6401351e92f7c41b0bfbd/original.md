```
split_by_season(dates::AbstractArray{<: Dates.DateTime})
```

Return four vectors with `dates` split by seasons.

The months of the seasons are March to May, June to August, September to November, and December to February. The order of the tuple is MAM, JJA, SON, and DJF.

# Examples

```jldoctest
julia> import Dates

julia> dates = [Dates.DateTime(2024, 1, 1), Dates.DateTime(2024, 3, 1), Dates.DateTime(2024, 6, 1), Dates.DateTime(2024, 9, 1)];

julia> split_by_season(dates)
([Dates.DateTime("2024-03-01T00:00:00")], [Dates.DateTime("2024-06-01T00:00:00")], [Dates.DateTime("2024-09-01T00:00:00")], [Dates.DateTime("2024-01-01T00:00:00")])
```
