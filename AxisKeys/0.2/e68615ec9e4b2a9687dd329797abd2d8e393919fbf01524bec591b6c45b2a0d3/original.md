```
Near(val)
Interval(lo, hi)
```

These selectors modify lookup using `axiskeys(A)`: `B(time = Near(3))` matches one entry with minimum `abs(t-3)` of named dimension `:time`. `C("cat", Interval(10,20))` matches all entries with `10 <= iter <= 20`).

`Interval` is from IntervalSets.jl, and using that you may also write `lo .. hi`, as well as `mid ± δ`.

```
==(val)
<(val)
```

Any functions can be used similarly, like C(!=("dog"), <=(33)). They ultimately call `findall(==(val), axiskeys(A,d))`.

Functions of type `Base.Fix2`, and `Selector`s, also allow a dimension to be chosen by type: `A(<=(3.1))` will work provided that only one of `map(eltype, axiskeys(A))` matches `typeof(3.1)`.

# Examples

```jldoctest
julia> v = KeyedArray(Symbol.('a':'e'), 10:10:50)
1-dimensional KeyedArray(...) with keys:
↓   5-element StepRange{Int64,...}
And data, 5-element Vector{Symbol}:
 (10)  :a
 (20)  :b
 (30)  :c
 (40)  :d
 (50)  :e

julia> v[Near(33)]
:c

julia> v[==(30)]  # all matching this key
1-dimensional KeyedArray(...) with keys:
↓   1-element Vector{Int64}
And data, 1-element Vector{Symbol}:
 (30)  :c

julia> v[Interval(17, 31)]
1-dimensional KeyedArray(...) with keys:
↓   2-element StepRange{Int64,...}
And data, 2-element Vector{Symbol}:
 (20)  :b
 (30)  :c

julia> m = wrapdims(hcat(v,v), x=nothing, y=[:left, :right]);

julia> m(<(30))  # selects 1st dim by type, and makes a view
2-dimensional KeyedArray(NamedDimsArray(...)) with keys:
↓   x ∈ 2-element StepRange{Int64,...}
→   y ∈ 2-element Vector{Symbol}
And data, 2×2 view(::Matrix{Symbol}, 1:2, :) with eltype Symbol:
       (:left)  (:right)
 (10)    :a       :a
 (20)    :b       :b
```
