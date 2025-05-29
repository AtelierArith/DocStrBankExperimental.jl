```
peakproms(; [strict, min, max]) -> Function
```

Create a function, `f(pks::NamedTuple)`, that calculates and filters the peak prominences of a copy of its argument, `pks`, using any given keyword arguments.

# Examples

```jldoctest
julia> findmaxima([0,5,2,3,3,1,4,0]) |> peakproms(; min=2)
(indices = [2, 7], heights = [5, 4], data = [0, 5, 2, 3, 3, 1, 4, 0], proms = Union{Missing, Int64}[5, 3])
```
