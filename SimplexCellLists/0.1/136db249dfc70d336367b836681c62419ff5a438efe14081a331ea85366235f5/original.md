Map `f` to all pairs of nearby simplexes in a single group.

```julia
mapPairElements(
        f,
        output,
        s::SimplexCellList,
        group_idx::Integer,
        elements_type::Type{Simplex{N}},
        cutoff::Float32,
    ) where {N}
```

Apply function `f` to all unordered pairs of elements in group `group_idx` within cutoff range, and return the output of the final `f` call.

`f` is never called more than once per unordered pair. Which element is `x` and `y` in calls to `f` is implementation dependent.

### Mapped function `f`

The function f should have the same form as used in CellListMap.jl.

`i` is the element index of simplex `x`, `j` is the element index of simplex `y`. 

`d2` is an approximate `Float32` squared distance between `x` and `y`.

Except here `x` and `y` are `Simplex{N}`, `Simplex{M}`

```julia
    function f(x,y,i,j,d2,output)
        # update output
        return output
    end
```
