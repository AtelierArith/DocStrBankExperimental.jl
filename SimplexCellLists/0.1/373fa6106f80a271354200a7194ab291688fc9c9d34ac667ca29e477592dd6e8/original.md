Map `f` to all simplexes in a group close to a single simplex.

```julia
mapSimplexElements(
        f,
        output,
        s::SimplexCellList,
        x::Simplex{N},
        group_idx::Integer,
        elements_type::Type{Simplex{M}},
        cutoff::Float32,
    ) where {N, M}
```

Apply function `f` to all elements in group `group_idx` within the cutoff range of the simplex `x`, and return the output of the final `f` call.

`x` is always `x` and `i` is always 0, in calls to `f`.

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
