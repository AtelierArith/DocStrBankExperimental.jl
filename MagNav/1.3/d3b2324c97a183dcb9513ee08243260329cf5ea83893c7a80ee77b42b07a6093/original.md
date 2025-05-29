```
plsr_fit(x, y, k::Int = size(x,2), no_norm = falses(size(x,2));
         data_norms::Tuple = (zeros(1,1),zeros(1,1),[0.0],[0.0]),
         l_segs::Vector    = [length(y)],
         return_set::Bool  = false,
         silent::Bool      = false)
```

Fit a multi-input, multi-output (MIMO) partial least squares regression (PLSR) model to data with a specified output dimension. PLSR is a type of regularized linear regression where the number of components controls the strength of the regularization.

**Arguments:**

  * `x`:          `N` x `Nf` data matrix (`Nf` is number of features)
  * `y`:          length-`N` target vector
  * `k`:          (optional) number of components
  * `no_norm`:    (optional) length-`Nf` Boolean indices of features to not be normalized
  * `data_norms`: (optional) length-`4` tuple of data normalizations, `(x_bias,x_scale,y_bias,y_scale)`
  * `l_segs`:     (optional) length-`N_lines` vector of lengths of `lines`, sum(l_segs) = `N`
  * `return_set`: (optional) if true, return `coef_set` instead of other outputs
  * `silent`:     (optional) if true, no print outs

**Returns:**

  * `model`:      length-`2` tuple of PLSR-based model, (length-`Nf` coefficients, bias=`0`)
  * `data_norms`: length-`4` tuple of data normalizations, `(x_bias,x_scale,y_bias,y_scale)`
  * `y_hat`:      length-`N` prediction vector
  * `err`:        length-`N` mean-corrected (per line) error
  * `coef_set`:   if `return_set = true`, set of coefficients (size `Nf` x `Ny` x `k`)
