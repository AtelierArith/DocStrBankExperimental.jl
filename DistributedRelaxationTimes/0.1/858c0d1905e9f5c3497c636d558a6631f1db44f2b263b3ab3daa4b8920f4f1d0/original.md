```
compute_DRT(frequencies, measurements; <keyword arguments>)
```

Calculate the Distribution of Relaxation Times using RBF discretization and Tikhonov regularisation.

The essential inputs are a set of frequencies and the impedance measurements conducted at those frequencies. There are also a number of keyword arguments to fine-tune the calculation. 

## Keyword arguments

  * `method::String="im"`: the part of the measurements used to calculate the DRT.
  * `rbf_kernel = SqExponentialKernel()`: The RBF used to discretize the DRT.
  * `width_coeff::Float64=0.10`: the hyperparameter influencing the shape factor of the RBF.
  * `λ::Float64=1e-2`: a hyperparameter tuning the degree of regularisation.
  * `peak_strictness::Float64=0.01`: A measure to avoid artifacts in the DRT by removing peaks           with amplitude less than a given percentage of the highest peak.

```

```
