```
Positional <: AbstractPositionalStencil

Positional(offsets::Tuple{Vararg{Int}}...)
Positional(offsets::Tuple{Tuple{Vararg{Int}}})
Positional{O}()
```

Stencils that can take arbitrary shapes by specifying each coordinate, as `Tuple{Int,Int}` of the row/column distance (positive and negative) from the central point.

The stencil radius is calculated from the most distant coordinate, and the dimensionality `N` of the stencil is taken from the length of the first coordinate, e.g. `1`, `2` or `3`.

See [`NamedStencil`](@ref) for a similar stencil with named offsets.

## Example

```julia
julia> p = Positional((0, -1), (2, 1), (-1, 1), (0, 1)) 
Positional{((0, -1), (2, 1), (-1, 1), (0, 1)), 2, 2, 4, Nothing}
   ▄ 
 ▀ ▀ 
   ▀ 
```
