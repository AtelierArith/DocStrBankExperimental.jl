```
elasticnet_fit(x, y, α::Real = 0.99, no_norm = falses(size(x,2));
               λ::Real           = -1,
               data_norms::Tuple = (zeros(1,1),zeros(1,1),[0.0],[0.0]),
               l_segs::Vector    = [length(y)],
               silent::Bool      = false)
```

Fit an elastic net (ridge regression and/or Lasso) model to data.

**Arguments:**

  * `x`:          `N` x `Nf` data matrix (`Nf` is number of features)
  * `y`:          length-`N` target vector
  * `α`:          (optional) ridge regression (`α=0`) vs Lasso (`α=1`) balancing parameter {0:1}
  * `no_norm`:    (optional) length-`Nf` Boolean indices of features to not be normalized
  * `λ`:          (optional) elastic net parameter, `-1` to ignore & determine with cross-validation
  * `data_norms`: (optional) length-`4` tuple of data normalizations, `(x_bias,x_scale,y_bias,y_scale)`
  * `l_segs`:     (optional) length-`N_lines` vector of lengths of `lines`, sum(l_segs) = `N`
  * `silent`:     (optional) if true, no print outs

**Returns:**

  * `model`:      length-`2` tuple of elastic net-based model, (length-`Nf` coefficients, bias)
  * `data_norms`: length-`4` tuple of data normalizations, `(x_bias,x_scale,y_bias,y_scale)`
  * `y_hat`:      length-`N` prediction vector
  * `err`:        length-`N` mean-corrected (per line) error
