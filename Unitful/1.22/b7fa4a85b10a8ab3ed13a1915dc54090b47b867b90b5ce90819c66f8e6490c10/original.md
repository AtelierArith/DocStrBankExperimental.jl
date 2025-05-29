```
Quantity(period::Dates.FixedPeriod)
```

Create a `Quantity` that corresponds to the given `period`. The numerical value of the resulting `Quantity` is of type `Int64`.

# Example

```jldoctest
julia> using Dates: Second

julia> Quantity(Second(5))
5 s
```
