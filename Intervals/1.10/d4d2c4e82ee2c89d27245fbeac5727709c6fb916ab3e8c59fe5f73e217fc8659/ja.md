```
IntervalSet{T<:AbstractInterval}
```

区間の列によって表される点の集合。区間集合に対する集合演算は、新しいIntervalSetを返し、可能な限り少ない数の区間を持ちます。無限区間はサポートされていません。集合内の個々の区間には、`convert(Array, interval_set)`を呼び出すことでアクセスできます。

関連情報: https://en.wikipedia.org/wiki/Interval*arithmetic#Interval*operators

## 例

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
