```
linear_test(x_norm, y, y_bias, y_scale, model::Tuple;
            l_segs::Vector = [length(y)],
            silent::Bool   = false)
```

Evaluate performance of a linear model.

**Arguments:**

  * `x_norm`:  `N` x `Nf` normalized data matrix (`Nf` is number of features)
  * `y`:       length-`N` target vector
  * `y_bias`:  `y` target vector bias bias (mean, min, or zero)
  * `y_scale`: `y` target vector bias scaling factor (std dev, max-min, or one)
  * `model`:   length-`2` tuple of model, (length-`Nf` coefficients, bias)
  * `l_segs`:  (optional) length-`N_lines` vector of lengths of `lines`, sum(l_segs) = `N`
  * `silent`:  (optional) if true, no print outs

**Returns:**

  * `y_hat`: length-`N` prediction vector
  * `err`:   length-`N` mean-corrected (per line) error
