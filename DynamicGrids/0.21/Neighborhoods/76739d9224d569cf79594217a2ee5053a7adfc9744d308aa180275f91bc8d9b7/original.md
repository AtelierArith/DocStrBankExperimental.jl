```
Positional <: AbstractPositionalNeighborhood

Positional(coord::Tuple{Vararg{Int}}...)
Positional(offsets::Tuple{Tuple{Vararg{Int}}})
Positional{O}()
```

Neighborhoods that can take arbitrary shapes by specifying each coordinate, as `Tuple{Int,Int}` of the row/column distance (positive and negative) from the central point.

The neighborhood radius is calculated from the most distant coordinate. For simplicity the window read from the main grid is a square with sides `2r + 1` around the central point.

The dimensionality `N` of the neighborhood is taken from the length of the first coordinate, e.g. `1`, `2` or `3`.

Example radius `R = 1`:

```
N = 1   N = 2

 ▄▄      ▀▄
          ▀
```

Example radius `R = 2`:

```
N = 1   N = 2

         ▄▄
 ▀ ▀▀   ▀███
           ▀
```

Using the `O` parameter e.g. `Positional{((1, 2), (1, 1))}()` removes any runtime cost of generating the neighborhood.
