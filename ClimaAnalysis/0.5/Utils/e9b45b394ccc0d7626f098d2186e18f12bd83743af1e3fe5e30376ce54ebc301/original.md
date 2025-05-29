```
split_by_season_across_time(dates::AbstractArray{<:Dates.DateTime})
```

Split `dates` into vectors representing seasons, arranged in chronological order. Each vector corresponds to a single season and the ordering of the vectors is determined by the dates of the season. The return type is a vector of vectors of dates.

If no dates are found for a particular season, then the vector will be empty. The first vector is guaranteed to be non-empty.

This function differs from `split_by_season` as `split_by_season` splits dates into different seasons and ignores that dates could come from seasons in different years. In contrast, `split_by_season_across_time` splits dates into seasons for each year.

# Examples

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
