```
TVRegularization
```

Regularization term implementing the proximal map for TV regularization. Calculated with the Condat algorithm if the TV is calculated only along one real-valued dimension and with the Fast Gradient Projection algorithm otherwise.

Reference for the Condat algorithm: https://lcondat.github.io/publis/Condat-fast_TV-SPL-2013.pdf

Reference for the FGP algorithm: A. Beck and T. Teboulle, "Fast Gradient-Based Algorithms for Constrained Total Variation Image Denoising and Deblurring Problems", IEEE Trans. Image Process. 18(11), 2009

# Arguments

  * `λ::T`                    - regularization parameter

# Keywords

  * `shape::NTuple`           - size of the underlying image
  * `dims`                    - Dimension to perform the TV along. If `Integer`, the Condat algorithm is called, and the FDG algorithm otherwise.
  * `iterationsTV=20`         - number of FGP iterations
