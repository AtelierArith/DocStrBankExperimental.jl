```
IntervalSet{T<:AbstractInterval}
```

A set of points represented by a sequence of intervals. Set operations over interval sets return a new IntervalSet, with the fewest number of intervals possible. Unbounded intervals are not supported. The individual intervals in the set can be accessed by calling `convert(Array, interval_set)`.

see also: https://en.wikipedia.org/wiki/Interval*arithmetic#Interval*operators

## Examples

```jldoctest; setup = :(using Intervals)
julia> union(IntervalSet(1..5), IntervalSet(3..8))
1-interval IntervalSet{Interval{Int64, Closed, Closed}}:
[1 .. 8]

julia> intersect(IntervalSet(1..5), IntervalSet(3..8))
1-interval IntervalSet{Interval{Int64, Closed, Closed}}:
[3 .. 5]

julia> symdiff(IntervalSet(1..5), IntervalSet(3..8))
2-interval IntervalSet{Interval{Int64, L, R} where {L<:Bound, R<:Bound}}:
[1 .. 3)
(5 .. 8]

julia> union(IntervalSet([1..2, 2..5]), IntervalSet(6..7))
2-interval IntervalSet{Interval{Int64, Closed, Closed}}:
[1 .. 5]
[6 .. 7]

julia> union(IntervalSet([1..5, 8..10]), IntervalSet([4..9, 12..14]))
2-interval IntervalSet{Interval{Int64, Closed, Closed}}:
[1 .. 10]
[12 .. 14]

julia> intersect(IntervalSet([1..5, 8..10]), IntervalSet([4..9, 12..14]))
2-interval IntervalSet{Interval{Int64, Closed, Closed}}:
[4 .. 5]
[8 .. 9]

julia> setdiff(IntervalSet([1..5, 8..10]), IntervalSet([4..9, 12..14]))
2-interval IntervalSet{Interval{Int64, L, R} where {L<:Bound, R<:Bound}}:
[1 .. 4)
(9 .. 10]
```
