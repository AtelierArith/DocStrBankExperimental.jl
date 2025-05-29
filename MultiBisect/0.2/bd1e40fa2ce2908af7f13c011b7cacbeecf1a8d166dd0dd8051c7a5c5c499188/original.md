```
bisect(f, grid; threaded=false, monotonic=false, iterations=5, verbose=false)
```

Perform the multidimensional bisection algorithm of function `f` on an initial `grid` of evaluation points.

# Arguments

## Positional Arguments

  * `f`: function to be evaluated
  * `grid`: a tuple of ranges describing the initial evaluation grid

## Keyword Arguments

  * `threaded`: set to `true` for multithreaded evaluation
  * `monotonic`: set to true if `f` is known to be monotonic in each dimension
  * `iterations`: number of times to iterate the algorithm
  * `verbose`: set to `true` to print the number of new function evaluations at each iteration

# Examples

```jldoctest
julia> grid = (0.0:1.0, 0.0:1.0);

julia> bisect(x -> 1 - sum(abs2, x), grid)
BisectionGrid{Float64, 2}
       Domain: (0.0:0.0625:1.0, 0.0:0.0625:1.0)
  Grid points: 289
  Evaluations: 112
        Edges: 32


julia> bisect(x -> x[2] - x[1], grid)
BisectionGrid{Float64, 2}
       Domain: (0.0:0.0625:1.0, 0.0:0.0625:1.0)
  Grid points: 289
  Evaluations: 112
        Edges: 32


julia> bisect(x -> x[2] - x[1], grid; monotonic=true)
BisectionGrid{Float64, 2}
       Domain: (0.0:0.0625:1.0, 0.0:0.0625:1.0)
  Grid points: 289
  Evaluations: 67
        Edges: 32
```

# Extended help

## Algorithm

The algorithm begins with an initial evaluation grid of $N$-dimensional hypercubes (lines, squares, cubes, etc.) and proceeds by splitting it in "half" at each stage, but only in regions where the function is known to change sign. After the function is evaluated, each hypercube is split in half (a line into two lines, a square into four squares, a cube into eight cubes, etc.) and the function sign at each vertex is checked. If not all vertices share the same sign, the function must change sign somewhere within the hypercube, so the vertices of the subcubes (e.g. the midpoint of a line) will be marked for evaluation in the next stage; if the vertices all share the same sign, the function is presumed to have the same sign everywhere throughout the hypercube, so the sign is inferred at all interior points and the function is not evaluated in the hypercube again.

By passing the keyword `monotonic=true`, the algorithm further assumes that the function cannot change sign in any one direction between two points with the same sign. This means that the sign of the function should be checked at the vertices of each edge of the hypercube; if the signs are the same, the function is assumed to have the same sign at the midpoint along the edge and will not be evaluated.

## Multithreading

Set the keyword argument `threaded=true` to make evaluation of the function at each iteration multithreaded. For functions that are very cheap to evaluate, the overhead from setting up threads will actually make each iteration longer. However, this effect disappears quickly.

### Example

```julia-repl
julia> ffast(x) = 1 - sum(abs2, x);

julia> grid = (0.0:1.0, 0.0:1.0);

julia> @btime bisect(ffast, $grid; threaded=false);
  49.720 μs (40 allocations: 3.59 KiB)

julia> @btime bisect(ffast, $grid; threaded=true);
  146.173 μs (163 allocations: 18.23 KiB)

julia> fslow(x) = (sleep(0.1); ffast(x))
fslow (generic function with 1 method)

julia> @btime bisect(fslow, $grid; threaded=false);
  11.397 s (605 allocations: 20.83 KiB)

julia> @btime bisect(fslow, $grid; threaded=true);
  3.170 s (736 allocations: 35.45 KiB)
```

## Monotonicity

If the function `f` is known to be monotonic, then the number of evaluations can be reduced by inferring the behavior of `f` along edges where both vertices have the same sign.

### Example

```jldoctest
julia> bisect(x -> 1 - sum(abs2, x), (0.0:1.0, 0.0:1.0); monotonic=false)
BisectionGrid{Float64, 2}
       Domain: (0.0:0.0625:1.0, 0.0:0.0625:1.0)
  Grid points: 289
  Evaluations: 112
        Edges: 32


julia> bisect(x -> 1 - sum(abs2, x), (0.0:1.0, 0.0:1.0); monotonic=true)
BisectionGrid{Float64, 2}
       Domain: (0.0:0.0625:1.0, 0.0:0.0625:1.0)
  Grid points: 289
  Evaluations: 80
        Edges: 32
```

## Iterations

For finer grids, repeat the algorithm for more iterations.

### Example

```jldoctest
julia> bisect(x -> 1 - sum(abs2, x), (0.0:1.0, 0.0:1.0))
BisectionGrid{Float64, 2}
       Domain: (0.0:0.0625:1.0, 0.0:0.0625:1.0)
  Grid points: 289
  Evaluations: 112
        Edges: 32


julia> bisect(x -> 1 - sum(abs2, x), (0.0:1.0, 0.0:1.0); iterations=3)
BisectionGrid{Float64, 2}
       Domain: (0.0:0.25:1.0, 0.0:0.25:1.0)
  Grid points: 25
  Evaluations: 22
        Edges: 8


julia> bisect(x -> 1 - sum(abs2, x), (0.0:1.0, 0.0:1.0); iterations=7)
BisectionGrid{Float64, 2}
       Domain: (0.0:0.015625:1.0, 0.0:0.015625:1.0)
  Grid points: 4225
  Evaluations: 490
        Edges: 128
```

## Logging

For longer-running bisections, it may be useful to report the number of new evaluations as a kind of thread-safe progress meter.

### Example

```jldoctest
julia> bisect(x -> 1 - sum(abs2, x), (0.0:1.0, 0.0:1.0); verbose=true)
[ Info: Iteration 1: 4 gridpoints (4 evaluations)
[ Info: Iteration 2: 9 gridpoints (5 evaluations)
[ Info: Iteration 3: 25 gridpoints (13 evaluations)
[ Info: Iteration 4: 81 gridpoints (29 evaluations)
[ Info: Iteration 5: 289 gridpoints (61 evaluations)
BisectionGrid{Float64, 2}
       Domain: (0.0:0.0625:1.0, 0.0:0.0625:1.0)
  Grid points: 289
  Evaluations: 112
        Edges: 32


julia> bisect(x -> 1 - sum(abs2, x), (0.0:1.0, 0.0:1.0); verbose=true, iterations=7)
[ Info: Iteration 1: 4 gridpoints (4 evaluations)
[ Info: Iteration 2: 9 gridpoints (5 evaluations)
[ Info: Iteration 3: 25 gridpoints (13 evaluations)
[ Info: Iteration 4: 81 gridpoints (29 evaluations)
[ Info: Iteration 5: 289 gridpoints (61 evaluations)
[ Info: Iteration 6: 1089 gridpoints (125 evaluations)
[ Info: Iteration 7: 4225 gridpoints (253 evaluations)
BisectionGrid{Float64, 2}
       Domain: (0.0:0.015625:1.0, 0.0:0.015625:1.0)
  Grid points: 4225
  Evaluations: 490
        Edges: 128
```
