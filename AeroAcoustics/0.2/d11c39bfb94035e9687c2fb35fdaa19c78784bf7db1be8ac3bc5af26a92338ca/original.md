```
fista(env::Environment,b ,p [,f<:AbstractArray]; tol=1e-6, maxit=1000)
```

Performs deconvolution with FISTA with a nonnegativity constraint for all frequency bins in `env.fn` or frequencies in `f`. `f` must contain values that match exact a (sub)set of the values in `env.fn`. 

# Arguments

*Required:*

  * `env::Environment`: Environment struct
  * `b::FreqArray`: Beamforming array
  * `p::FreqArray`: Point spread function array

*Optional:*

  * `tol`: Convergence tolerance (default: 1e-6)
  * `maxit`: Maximum number of iterations (default: 1000)

# References:

  * Beck, A., & Teboulle, M. (2009). A fast iterative shrinkage-thresholding algorithm for linear inverse problems.    SIAM journal on imaging sciences, 2(1), 183-202.
  * Lylloff, O., Fernández-Grande, E., Agerkvist, F., Hald, J., Tiana Roig, E., & Andersen, M. S. (2015). Improving the efficiency of deconvolution algorithms for sound source localization.    The journal of the acoustical society of America, 138(1), 172-180
