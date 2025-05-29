Map `f` to all pairs of nearby simplexes between two different groups.

```julia
mapElementsElements(
        f, 
        output, 
        s::SimplexCellList, 
        x_group_idx::Integer, 
        x_type::Type{Simplex{N}}, 
        y_group_idx::Integer, 
        y_type::Type{Simplex{M}}, 
        cutoff::Float32,
    ) where {N, M}
```

Apply function `f` to each pair of elements from two different groups that are within cutoff range of each other, and return the output of the final `f` call.

The first element has is an `x_type` in group `x_group_idx` and the second element is a `y_type` in group `y_group_idx`.

`f` is never called more than once per pair.

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
