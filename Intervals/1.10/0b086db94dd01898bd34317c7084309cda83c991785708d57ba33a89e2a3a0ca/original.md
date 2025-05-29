```
AnchoredInterval{P,T,L,R}
```

`AnchoredInterval` is a subtype of `AbstractInterval` that represents a non-iterable range or span of values defined not by two endpoints but instead by a single `anchor` point and the value type `P` which represents the size of the range. When `P` is positive, the `anchor` represents the lesser endpoint (the beginning of the range); when `P` is negative, the `anchor` represents the greater endpoint (the end of the range).

The interval represented by an `AnchoredInterval` value may be closed (both endpoints are included in the interval), open (neither endpoint is included), or half-open. This openness is defined by the bounds types `L` and `R`, which defaults to half-open (with the lesser endpoint included for positive values of `P` and the greater endpoint included for negative values).

### Why?

`AnchoredIntervals` are most useful in cases where a single value is used to stand in for a range of values. This happens most often with dates and times, where "HE15" is often used as shorthand for (14:00..15:00].

To this end, `HourEnding` is a type alias for `AnchoredInterval{Hour(-1)}`. Similarly, `HourBeginning` is a type alias for `AnchoredInterval{Hour(1)}`.

### Rounding

While the user may expect an `HourEnding` or `HourBeginning` value to be anchored to a specific hour, the constructor makes no guarantees that the anchor provided is rounded:

```jldoctest; setup = :(using Intervals, Dates), filter = r"AnchoredInterval\{(Day|Hour|Minute)\(-?\d+\),|Hour(Ending|Beginning)\{"
julia> HourEnding(DateTime(2016, 8, 11, 2, 30))
HourEnding{DateTime, Open, Closed}(DateTime("2016-08-11T02:30:00"))
```

The `HE` and `HB` pseudoconstructors round the input up or down to the nearest hour, as appropriate:

```jldoctest; setup = :(using Intervals, Dates), filter = r"AnchoredInterval\{(Day|Hour|Minute)\(-?\d+\),|Hour(Ending|Beginning)\{"
julia> HE(DateTime(2016, 8, 11, 2, 30))
HourEnding{DateTime, Open, Closed}(DateTime("2016-08-11T03:00:00"))

julia> HB(DateTime(2016, 8, 11, 2, 30))
HourBeginning{DateTime, Closed, Open}(DateTime("2016-08-11T02:00:00"))
```

### Example

```jldoctest; setup = :(using Intervals, Dates), filter = r"AnchoredInterval\{(Day|Hour|Minute)\(-?\d+\),|Hour(Ending|Beginning)\{"
julia> AnchoredInterval{Hour(-1)}(DateTime(2016, 8, 11, 12))
HourEnding{DateTime, Open, Closed}(DateTime("2016-08-11T12:00:00"))

julia> AnchoredInterval{Day(1)}(DateTime(2016, 8, 11))
AnchoredInterval{Day(1), DateTime, Closed, Open}(DateTime("2016-08-11T00:00:00"))

julia> AnchoredInterval{Minute(5),Closed,Closed}(DateTime(2016, 8, 11, 12, 30))
AnchoredInterval{Minute(5), DateTime, Closed, Closed}(DateTime("2016-08-11T12:30:00"))
```

See also: [`Interval`](@ref), [`HE`](@ref), [`HB`](@ref)
