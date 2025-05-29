# Circulant convolution operator

The circulant convolution operator `H` is defined by:

```julia
H  = (1/n)*F'*Diag(mtf)*F
```

with `n` the number of elements, `F` the discrete Fourier transform operator and `mtf` the modulation transfer function.

The operator `H` can be created by:

```julia
H = CirculantConvolution(psf; flags=FFTW.MEASURE, timelimit=Inf, shift=false)
```

where `psf` is the point spread function (PSF).  Note that the PSF is assumed to be centered according to the convention of the discrete Fourier transform. You may use `ifftshift` or the keyword `shift` if the PSF is geometrically centered:

```julia
H = CirculantConvolution(ifftshift(psf))
H = CirculantConvolution(psf, shift=true)
```

The following keywords can be specified:

  * `shift` (`false` by default) indicates whether to apply `ifftshift` to `psf`.
  * `normalize` (`false` by default) indicates whether to divide `psf` by the sum of its values.  This keyword is only available for real-valued PSF.
  * `flags` is a bitwise-or of FFTW planner flags, defaulting to `FFTW.MEASURE`. If the operator is to be used many times (as in iterative methods), it is recommended to use at least `flags=FFTW.MEASURE` (the default) which generally yields faster transforms compared to `flags=FFTW.ESTIMATE`.
  * `timelimit` specifies a rough upper bound on the allowed planning time, in seconds.

The operator can be used as a regular linear operator: `H(x)` or `H*x` to compute the convolution of `x` and `H'(x)` or `H'*x` to apply the adjoint of `H` to `x`.

For a slight improvement of performances, an array `y` to store the result of the operation can be provided:

```julia
apply!(y, [P=Direct,] H, x) -> y
apply!(y, H, x)
apply!(y, H', x)
```

If provided, `y` must be at a different memory location than `x`.
