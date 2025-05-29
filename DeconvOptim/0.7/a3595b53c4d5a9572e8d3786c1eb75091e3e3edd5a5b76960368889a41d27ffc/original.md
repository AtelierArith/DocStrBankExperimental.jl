```
deconvolution(measured, psf; <keyword arguments>)
```

Computes the deconvolution of `measured` and `psf`. Return parameter is a tuple with two elements. The first entry is the deconvolved image. The second return parameter  is the output of the optimization of Optim.jl

Multiple keyword arguments can be specified for different loss functions, regularizers and mappings.

# Arguments

  * `loss=Poisson()`: the loss function taking a vector the same shape as measured.
  * `regularizer=nothing`: A regularizer function, same form as `loss`.    See `GR`, `TV`, `Tikhonov` and the help page for different regularizers.
  * `λ=0.05`: A float indicating the total weighting of the regularizer with    respect to the global loss function
  * `background=0`: A float indicating a background intensity level.
  * `mapping=Non_negative()`: Applies a mapping of the optimizer weight. Default is a              parabola which achieves a non-negativity constraint.
  * `iterations=nothing`: Specifies a number of iterations after the optimization.   definitely should stop. By default 20 iterations will be selected by generic_invert.jl,    if `nothing` is provided.
  * `conv_dims`: A tuple indicating over which dimensions the convolution should happen.              per default `conv_dims=1:ndims(psf)`
  * `plan_fft=true`: Boolean whether plan_fft is used. Gives a slight speed improvement.
  * `padding=0`: an float indicating the amount (fraction of the size in that dimension)    of padded regions around the reconstruction. Prevents wrap around effects of the FFT.   A array with `size(arr)=(400, 400)` with `padding=0.05` would result in reconstruction size of    `(440, 440)`. However, if padding is >= 0.0, we only return the reconstruction cropped to the original size.   For negative paddings, the absolute value is used, but the result maintains the padded size.   `padding=0` disables any padding.
  * `opt_package=Opt_Optim`: decides which backend for the optimizer is used.
  * `opt=LBFGS()`: The chosen optimizer which must fit to `opt_package`
  * `opt_options=nothing`: Can be a options file required by Optim.jl. Will overwrite iterations.
  * `initial=mean(measured)`: defines a value (or array) with the initial guess. This will be pulled through the inverse mapping function                    and extended with a mean value (if border regions are used).
  * `debug_f=nothing`: A debug function which must take a single argument, the current reconstruction.

!!! note
    If you want to provide your PSF model, ensure that centered around the first entry of the array (`psf[1]`). You may need to use `ifftshift` for a PSF model or a measured PSF.


# Example

```julia-repl
julia> using DeconvOptim, TestImages, Colors, Noise;

julia> img = Float32.(testimage("resolution_test_512"));

julia> psf = Float32.(generate_psf(size(img), 30));

julia> img_b = conv(img, psf);

julia> img_n = poisson(img_b, 300);

julia> res, o = deconvolution(img_n, psf);
```
