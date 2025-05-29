```
timeseriessimplices(time::AbstractVector; groupby::AbstractVector)
```

Create SimplexGraph connecting elements adjacent in time. In case of ties, **all** elements at a unique timepoint will be connected to the **all** elements at the previous, current and next timepoints. If `groupby` is specified, the elements are first divided by group, and then connected by time.

# Examples

```
julia> sg = timeseriessimplices([0.5, 1.0, 4.0]);

julia> sg.G
3×3 BitArray{2}:
 1  1  0
 1  1  1
 0  1  1

julia> sg = timeseriessimplices([0.5, 1.0, 1.0, 4.0]);

julia> sg.G
4×3 BitArray{2}:
 1  1  0
 1  1  1
 1  1  1
 0  1  1

julia> sg.w
3-element Array{Int64,1}:
 1
 2
 1

julia> sg = timeseriessimplices([2, 4, 6, 2, 4, 8]; groupby=["A","A","A","B","B","B"]);

julia> sg.G
6×6 BitArray{2}:
 1  1  0  0  0  0
 1  1  1  0  0  0
 0  1  1  0  0  0
 0  0  0  1  1  0
 0  0  0  1  1  1
 0  0  0  0  1  1
```
