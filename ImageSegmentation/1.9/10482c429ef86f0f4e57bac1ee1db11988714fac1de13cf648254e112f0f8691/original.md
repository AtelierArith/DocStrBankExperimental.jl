```
flood_fill!(f, dest, src, idx, nbrhood_function=diamond_iterator((3,3,...)); fillvalue=true, isfilled = isequal(fillvalue))
```

Set entries of `dest` to `fillvalue` for all elements of `src` that:

  * satisfy `f(src[i]) == true` and
  * are connected by such elements to the starting point `idx` (an integer index or `CartesianIndex`).

This throws an error if `f` evaluates as `false` for the starting value `src[idx]`. The sense of connectivity is defined by `nbrhood_function`, with two choices being [`ImageSegmentation.diamond_iterator`](@ref) and [`ImageSegmentation.box_iterator`](@ref.)

You can optionally omit `dest`, in which case entries in `src` will be set to `fillvalue`. This is recommended only in cases where `fillvalue` is distinct from the values in `src`, as otherwise there is a risk that some voxels will be incorrectly identified as having been visited and their neighbors excluded from further search. You may also supply `isfilled`, which should return `true` for any value in `dest` which does not need to be set or visited; one requirement is that `isfilled(fillvalue) == true`.

# Examples

```jldoctest; setup=:(using ImageSegmentation)
julia> a = repeat([1:4; 1:4], 1, 3)
8×3 Matrix{Int64}:
 1  1  1
 2  2  2
 3  3  3
 4  4  4
 1  1  1
 2  2  2
 3  3  3
 4  4  4

julia> flood_fill!(>=(3), a, CartesianIndex(3, 2); fillvalue = -1, isfilled = <(0))
8×3 Matrix{Int64}:
  1   1   1
  2   2   2
 -1  -1  -1
 -1  -1  -1
  1   1   1
  2   2   2
  3   3   3
  4   4   4
```

See also [`flood`](@ref).
