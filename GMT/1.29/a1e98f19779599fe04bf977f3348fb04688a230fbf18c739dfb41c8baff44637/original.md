```
D = density(x::Vector{<:Real}; nbins::Integer=200, bins::Vector{<:Real}=Vector{Real}(),
            bandwidth=nothing, kernel::StrSymb="normal")
```

  * `x`: calculate the kernel density 'd' of a dataset X for query points 'xd' The density, by default, is   estimated using a gaussian kernel with a width obtained with the Silverman's rule. `x` may be   a vector, a matrix or Vector{Vector{Real}}.
  * `nbins`: points are queried between MIN(Y[:]) and MAX(Y[:]) where Y is the data vector.
  * `bins`: Calculates the density for the query points specified by BINS. The values are used as the   query points directly. Default is 200 points.
  * `bandwidth`: uses the 'bandwidth' to calculate the kernel density. It must be a scalar.   For the uniform case the bandwidth is set to 15% of the range, otherwise the bandwidth is chosen   with the Silverman's rule.
  * `printbw`: Logical value indicating to print the computed value of the `bandwidth`.
  * `kernel`: Uses the kernel function specified by KERNEL name (a string or a symbol) to calculate the density.   The kernel may be: 'Normal' (default) or 'Uniform'
  * `extend`: By default the density curve is computed at the `bins` locatins or between data extrema as   mentioned above. However, this is not normally enough to go down to zero. Use this option in terms of   number of bandwidth to expand de curve. *e.g.* `extend=2`

The version     G = density(data, x,y; weights=nothing, bandwidth=nothing, showbw=false)

Computes the smoothed kernel probability density estimate of a two-column matrix `data`. The estimate is based on a normal kernel function, and is evaluated at the points defined by the vectors `x` and `y`. The `showbw` option is used to print the bandwidth used. It returns a GMTgrid of the same size as `x` and `y`.

### Example

```julia
  X = [0.5*rand(20,1) 5 .+ 2.5*rand(20,1); .75 .+ 0.25*rand(10,1) 8.75 .+ 1.25*rand(10,1)]
  G = density(X, -0.25:.05:1.25, 0:.1:15)[1];
  viz(G, figsize=(12,12), view=(225,30))
```
