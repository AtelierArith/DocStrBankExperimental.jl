```
GreedyColoringAlgorithm{decompression} <: ADTypes.AbstractColoringAlgorithm
```

Greedy coloring algorithm for sparse matrices which colors columns or rows one after the other, following a configurable order.

It is passed as an argument to the main function [`coloring`](@ref).

# Constructors

```
GreedyColoringAlgorithm{decompression}(order=NaturalOrder(); postprocessing=false)
GreedyColoringAlgorithm(order=NaturalOrder(); postprocessing=false, decompression=:direct)
```

  * `order::AbstractOrder`: the order in which the columns or rows are colored, which can impact the number of colors.
  * `postprocessing::Bool`: whether or not the coloring will be refined by assigning the neutral color `0` to some vertices.
  * `decompression::Symbol`: either `:direct` or `:substitution`. Usually `:substitution` leads to fewer colors, at the cost of a more expensive coloring (and decompression). When `:substitution` is not applicable, it falls back on `:direct` decompression.

!!! warning
    The second constructor (based on keyword arguments) is type-unstable.


# ADTypes coloring interface

`GreedyColoringAlgorithm` is a subtype of [`ADTypes.AbstractColoringAlgorithm`](@extref ADTypes.AbstractColoringAlgorithm), which means the following methods are also applicable:

  * [`ADTypes.column_coloring`](@extref ADTypes.column_coloring)
  * [`ADTypes.row_coloring`](@extref ADTypes.row_coloring)
  * [`ADTypes.symmetric_coloring`](@extref ADTypes.symmetric_coloring)

See their respective docstrings for details.

# See also

  * [`AbstractOrder`](@ref)
  * [`decompress`](@ref)
