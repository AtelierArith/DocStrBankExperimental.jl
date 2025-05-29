```
NaturalNeighboursMethod(; method=Sibson(1), kwargs...)
```

Interpolator that uses the [NaturalNeighbours.jl](https://github.com/DanielVandH/NaturalNeighbours.jl) package to interpolate the data.  This uses Delaunay triangulations and  the corresponding Voronoi diagram to interpolate the data, and offers a variety of methods like `Sibson(::Int)`, `Nearest()`, and `Triangle()`.

The advantage of Voronoi-diagram based methods is that they are more robust to  irregularly distributed datasets and some discontinuities, which may throw off  some polynomial based methods as well as independent distance weighting (kriging).  See [this Discourse post](https://discourse.julialang.org/t/ann-naturalneighbours-jl-natural-neighbour-interpolation-and-derivative-generation/99164/11) for more information on why NaturalNeighbours are cool! 

To access the methods easily, you should run `using NearestNeighbours`.

See the [NaturalNeighbours documentation](https://github.com/DanielVandH/NaturalNeighbours.jl) for more details.

This method is fully configurable and will forward all arguments to the relevant NaturalNeighbours.jl functions. To understand what the methods do, see the documentation for [`NaturalNeighbours.jl`](https://github.com/DanielVandH/NaturalNeighbours.jl).

## Keyword arguments

The main keyword argument to look at here is `method`, which is the method to use for the interpolation.  The other keyword arguments are simply forwarded  to NaturalNeighbours.jl's interpolator.

  * `method`: The method to use for the interpolation.  Defaults to `Sibson(1). Default: NaturalNeighbours.Sibson{1}()
  * `parallel`: Whether to use multithreading when interpolating.  Defaults to `true`. Default: true
  * `project`: Whether to project the data onto the Delaunay triangulation.  Defaults to `true`. Default: true
  * `derivative_method`: The method to use for the differentiation.  Defaults to `Direct()`.  May be `Direct()` or `Iterative()`. Default: NaturalNeighbours.Direct()
  * `use_cubic_terms`: Whether to use cubic terms for estimating the second order derivatives. Only relevant for derivative_method == Direct(). Default: true
  * `alpha`: The weighting parameter used for estimating the second order derivatives. Only relevant for derivative_method == Iterative(). Default: 0.1
