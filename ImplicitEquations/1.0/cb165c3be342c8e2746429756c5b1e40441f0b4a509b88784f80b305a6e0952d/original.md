Function to graph, using ascii characters, a predicate related to a two-dimensional equation, such as `f == 0` or `f < g`, where `f` and `g` are functions, e.g., `f(x,y) = y - sqrt(x)`. The positional arguments are `L`, `R`, `B`, `T` which indicate the x-y range of the graph of the equation. The keyword arguments `W` and `H` indicate the number of pixels to use.

Set `offset=0` to see algorithm

A pixel is important, as the graph will color a pixel

  * "white" (e.g., " ") if no solution exists in the region indicated by the pixel
  * "black" (e.g., "x") if a solution is known to exist in the region
  * "red" (e.g. ".") if a solution *might* exist

## Example

```
julia> f(x,y) = x^2 + y^2
f (generic function with 1 method)

julia> r = f ⩵ 4^2
ImplicitEquations.Pred(f, ==, 16)

julia> asciigraph(r)

     .xxxxx
    xx    xx
   x.      xx
  x.        xx
 xx          xx
 x            x
 x            x
 x            x
 x            x
 xx          x.
  xx        .x
   xx      .x
    xx    xx
     xxxxx.

```
