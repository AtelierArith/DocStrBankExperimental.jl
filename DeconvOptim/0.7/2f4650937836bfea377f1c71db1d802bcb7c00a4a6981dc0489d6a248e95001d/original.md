```
richardson_lucy_iterative(measured, psf; <keyword arguments>)
```

Classical iterative Richardson-Lucy iteration scheme for deconvolution. `measured` is the measured array and `psf` the point spread function. Converges slower than the optimization approach of `deconvolution`

# Keyword Arguments

  * `regularizer=GR()`: A regularizer function. Can be exchanged
  * `λ=0.05`: A float indicating the total weighting of the regularizer with    respect to the global loss function
  * `iterations=100`: Specifies number of iterations.
  * `progress`: if not `nothing`, the progress will be monitored in a summary dictionary as obtained by             DeconvOptim.options*trace*deconv()

# Example

```julia-repl
julia> using DeconvOptim, TestImages, Colors, Noise;

julia> img = Float32.(testimage("resolution_test_512"));

julia> psf = Float32.(generate_psf(size(img), 30));

julia> img_b = conv(img, psf);

julia> img_n = poisson(img_b, 300);

julia> @time res = richardson_lucy_iterative(img_n, psf);
```
