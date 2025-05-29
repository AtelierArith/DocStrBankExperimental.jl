```
FourierDualDomain(imgdomain::AbstractRectiGrid, alg::FFTAlg)
```

Constructs a FourierDualDomain that uses the FFT algorithm to compute the transformation. For this no visibilty domain is specified since we assume it is the default grid from the FFT with padding specified in [`FFTAlg`](@ref).

## Arguments

  * `imgdomain`: The image domain grid
  * `alg`: The FFT algorithm to use
