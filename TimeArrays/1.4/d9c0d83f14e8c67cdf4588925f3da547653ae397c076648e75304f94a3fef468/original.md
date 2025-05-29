```
TimeArray(timestamps::Vector{TimeLike}, values::Vector{Any})
```

Creates a `TimeArray` by "zipping" together elements of `timestamps` and `values`.

## Examples

```jldoctest
julia> using Dates

julia> timestamps = [
           DateTime("2024-01-02"),
           DateTime("2024-01-03"),
           DateTime("2024-01-01"),
       ];

julia> values = [2.0, 1.0, 3.0];

julia> TimeArray(timestamps, values)
3-element TimeArray{DateTime, Float64}:
 TimeTick(2024-01-01T00:00:00, 3.0)
 TimeTick(2024-01-02T00:00:00, 2.0)
 TimeTick(2024-01-03T00:00:00, 1.0)
```
