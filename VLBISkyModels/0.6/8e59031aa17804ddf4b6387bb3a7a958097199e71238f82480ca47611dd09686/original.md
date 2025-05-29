```
FourierDualDomain(imgdomain::AbstractSingleDomain, visdomain::AbstractSingleDomain, algorithm)
```

Constructs a set of grids that live in the image and visibility domains. The transformation between the grids is specified by the `algorithm` which is a subtype of `VLBISkyModels.FourierTransform`.

# Arguments

  * `imgdomain`: The image domain grid
  * `visdomain`: The visibility domain grid
  * `algorithm`: The Fourier transform algorithm to use see `subtypes(VLBISkyModels.FourierTransform)` for a list
