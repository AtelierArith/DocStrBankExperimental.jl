```
getPriorParameters()
```

These are standard values for scale and shape of Inverse Gamma priors over kernel parameters, confounder structure covariance noise, and confounder Gaussian prior covariance. 

  * `uNoiseShape::Float64=4.0`: shape of the InvGamma prior over the noise of U
  * `uNoiseScale::Float64=4.0`: scale of the InvGamma prior over the noise of U
  * `xNoiseShape::Float64=4.0`: shape of the InvGamma prior over the noise of X
  * `xNoiseScale::Float64=4.0`: scale of the InvGamma prior over the noise of X
  * `tNoiseShape::Float64=4.0`: shape of the InvGamma prior over the noise of T
  * `tNoiseScale::Float64=4.0`: scale of the InvGamma prior over the noise of T
  * `yNoiseShape::Float64=4.0`: shape of the InvGamma prior over the noise of Y
  * `yNoiseScale::Float64=4.0`: scale of the InvGamma prior over the noise of Y
  * `xScaleShape::Float64=4.0`: shape of the InvGamma prior over kernel scale of X
  * `xScaleScale::Float64=4.0`: scale of the InvGamma prior over kernel scale of X
  * `tScaleShape::Float64=4.0`: shape of the InvGamma prior over kernel scale of T
  * `tScaleScale::Float64=4.0`: scale of the InvGamma prior over kernel scale of T
  * `yScaleShape::Float64=4.0`: shape of the InvGamma prior over kernel scale of Y
  * `yScaleScale::Float64=4.0`: scale of the InvGamma prior over kernel scale of Y
  * `uxLSShape::Float64=4.0`: shape of the InvGamma prior over kernel lengthscale of U and X
  * `uxLSScale::Float64=4.0`: scale of the InvGamma prior over kernel lengthscale of U and X
  * `utLSShape::Float64=4.0`: shape of the InvGamma prior over kernel lengthscale of U and T
  * `utLSScale::Float64=4.0`: scale of the InvGamma prior over kernel lengthscale of U and T
  * `xtLSShape::Float64=4.0`: shape of the InvGamma prior over kernel lengthscale of X and T
  * `xtLSScale::Float64=4.0`: scale of the InvGamma prior over kernel lengthscale of X and T
  * `uyLSShape::Float64=4.0`: shape of the InvGamma prior over kernel lengthscale of U and Y
  * `uyLSScale::Float64=4.0`: scale of the InvGamma prior over kernel lengthscale of U and Y
  * `xyLSShape::Float64=4.0`: shape of the InvGamma prior over kernel lengthscale of X and Y
  * `xyLSScale::Float64=4.0`: scale of the InvGamma prior over kernel lengthscale of X and Y
  * `tyLSShape::Float64=4.0`: shape of the InvGamma prior over kernel lengthscale of T and Y
  * `tyLSScale::Float64=4.0`: scale of the InvGamma prior over kernel lengthscale of T and Y
  * `sigmaUNoise::Float64=1.0e-13`: noise added to matrix to make covariance stable and invertible
  * `sigmaUCov::Float64=1.0`: assumed covariance over structured confounders
  * `drift::Float64=0.5`: as in the paper, Metropolis Hastings Gaussian Drift
