```
Interval{T, L <: Bound, R <: Bound}
```

An `Interval` represents a non-iterable range or span of values (non-iterable because, unlike a `StepRange`, no step is defined).

An `Interval` can be closed (both `first` and `last` are included in the interval), open (neither `first` nor `last` are included), or half-open. This openness is defined by the bounds information which is stored as the type parameters `L` and `R`.

### Example

```julia
julia> interval = Interval{Closed,Open}(0, 100)
Interval{Int64,Closed,Open}}(0, 100)

julia> 0 in interval
true

julia> 50 in interval
true

julia> 100 in interval
false

julia> intersect(Interval{Open,Open}(0, 25), Interval{Closed,Closed}(20, 50)
Interval{Int64,Closed,Open}(20, 25)
```

### Infix Constructor: `..`

A closed `Interval` can be constructed with the `..` infix constructor:

```julia
julia> Dates.today() - Dates.Week(1) .. Dates.today()
Interval{Date,Closed,Closed}(2018-01-24, 2018-01-31)
```

See also: [`AnchoredInterval`](@ref)
