```
krr_fit(x, y, no_norm = falses(size(x,2));
        k::Kernel           = PolynomialKernel(;degree=1),
        λ::Real             = 0.5,
        norm_type_x::Symbol = :standardize,
        norm_type_y::Symbol = :standardize,
        data_norms::Tuple   = (zeros(1,1),zeros(1,1),[0.0],[0.0]),
        l_segs::Vector      = [length(y)],
        silent::Bool        = false)
```

Fit a kernel ridge regression (KRR) model to data.

**Arguments:**

  * `x`:           `N` x `Nf` data matrix (`Nf` is number of features)
  * `y`:           length-`N` target vector
  * `no_norm`:     (optional) length-`Nf` Boolean indices of features to not be normalized
  * `k`:           (optional) kernel
  * `λ`:           (optional) ridge parameter
  * `norm_type_x`: (optional) normalization for `x` data matrix
  * `norm_type_y`: (optional) normalization for `y` target vector
  * `data_norms`:  (optional) length-`4` tuple of data normalizations, `(x_bias,x_scale,y_bias,y_scale)`
  * `l_segs`:      (optional) length-`N_lines` vector of lengths of `lines`, sum(l_segs) = `N`
  * `silent`:      (optional) if true, no print outs

**Returns:**

  * `model`:      length-`3` tuple of KRR-based model, (`k`, length-`N` coefficients, `N` x `Nf` data matrix, normalized)
  * `data_norms`: length-`4` tuple of data normalizations, `(x_bias,x_scale,y_bias,y_scale)`
  * `y_hat`:      length-`N` prediction vector
  * `err`:        length-`N` mean-corrected (per line) error
