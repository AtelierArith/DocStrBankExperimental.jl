```
get_std_errors(model::MSM)
```

Returns standard errors of the estimated parameters.  The errors are calculated with finite difference hessian od the log-likelihood function.

The output is a vector of standard errors in order given by `raw_params` field of the model.

The formula is squared diagonal values of the inverse (moore-penrose) of the hessian matrix:

$$
(-\frac{\partial^2 \mathcal{L}(\mathbf{\theta})}{\partial \mathbf{\theta} \mathbf{\theta}'})^{-1}
$$
