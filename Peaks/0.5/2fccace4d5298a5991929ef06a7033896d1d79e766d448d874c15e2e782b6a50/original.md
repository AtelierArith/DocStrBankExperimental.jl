```
filterpeaks!(pred, pks) -> NamedTuple
```

Apply a predicate function `pred` to NamedTuple slices (the scalar values related to each peak, e.g. `(indices=5, heights=3, proms=2)`) to and remove a peak if `pred` returns `false`.

# Examples

```jldoctest
julia> pks = findmaxima([0,5,2,3,3,1,4,0])
(indices = [2, 4, 7], heights = [5, 3, 4], data = [0, 5, 2, 3, 3, 1, 4, 0])

julia> filterpeaks!(pks) do nt
           return nt.heights ≥ 5 || nt.heights ≤ 3
       end
(indices = [2, 4], heights = [5, 3], data = [0, 5, 2, 3, 3, 1, 4, 0])
```
