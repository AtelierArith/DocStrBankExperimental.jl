```
peakwidths!(; [strict, relheight, min, max]) -> Function
```

Create a function, `f(pks::NamedTuple)`, that calculates and filters (mutates) the peak widths and other fields of its argument, `pks`, using any given keyword arguments.

# Examples

```jldoctest
julia> findmaxima([0,5,2,3,3,1,4,0]) |> peakproms!() |> peakwidths!(; min=1.5)
(indices = [4], heights = [3], data = [0, 5, 2, 3, 3, 1, 4, 0], proms = Union{Missing, Int64}[1], widths = Union{Missing, Float64}[1.75], edges = Tuple{Union{Missing, Float64}, Union{Missing, Float64}}[(3.5, 5.25)])
```
