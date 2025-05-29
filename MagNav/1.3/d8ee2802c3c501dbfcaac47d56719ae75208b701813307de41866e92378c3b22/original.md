```
linear_test(x, y, data_norms::Tuple, model::Tuple;
            l_segs::Vector = [length(y)],
            silent::Bool   = false)
```

Evaluate performance of a linear model.

**Arguments:**

  * `x`:          `N` x `Nf` data matrix (`Nf` is number of features)
  * `y`:          length-`N` target vector
  * `data_norms`: length-`4` tuple of data normalizations, `(x_bias,x_scale,y_bias,y_scale)`
  * `model`:      length-`2` tuple of model, (length-`Nf` coefficients, bias)
  * `l_segs`:     (optional) length-`N_lines` vector of lengths of `lines`, sum(l_segs) = `N`
  * `silent`:     (optional) if true, no print outs

**Returns:**

  * `y_hat`: length-`N` prediction vector
  * `err`:   length-`N` mean-corrected (per line) error
