difftime(time1::Union{DateTime, Missing}, time2::Union{DateTime, Missing}, units::AbstractString)

Calculate the difference between two times in the specified units.

# Arguments

`time1`: A DateTime object (can contain missing values in a DataFrame). `time2`: A DateTime object (can contain missing values in a DataFrame). `units`: A string specifying the units to use when calculating the difference between the two times. The units can be one of the following: "seconds", "minutes", "hours", "days", "weeks".

# Returns

The difference between the two times in the specified units. If either of the inputs is missing, the function returns a missing value.

# Examples

```jldoctest
julia> time1 = DateTime(2023, 6, 15, 9, 30, 0)
2023-06-15T09:30:00

julia> time2 = DateTime(2023, 6, 15, 8, 30, 0)
2023-06-15T08:30:00

julia> difftime(time1, time2, "hours")
1.0

julia> difftime(time1, time2, "minutes")
60.0

julia> difftime(time1, missing, "hours")
missing
```
