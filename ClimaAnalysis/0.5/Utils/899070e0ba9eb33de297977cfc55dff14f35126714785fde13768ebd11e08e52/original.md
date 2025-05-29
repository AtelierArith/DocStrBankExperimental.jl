```
split_by_month(dates::AbstractArray{<:Dates.DateTime})
```

Split `dates` into vectors representing months, arranged in chronological order. Each vector corresponds to a single month and the ordering of the vectors is determined by the dates of the season. The return type is a vector of vectors of dates.

If no dates are found for a particular season, then the vector will be empty.

# Examples

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
