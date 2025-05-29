```
norm_sets(train, val, test;
          norm_type::Symbol = :standardize,
          no_norm           = falses(size(train,2)))
```

Normalize (or standardize) features (columns) of training, validation, & testing data.

**Arguments:**

  * `train`:     `N_train` x `Nf` training data
  * `val`:       `N_val`   x `Nf` validation data
  * `test`:      `N_test`  x `Nf` testing data
  * `norm_type`: (optional) normalization type:

      * `:standardize` = Z-score normalization
      * `:normalize`   = min-max normalization
      * `:scale`       = scale by maximum absolute value, bias = 0
      * `:none`        = scale by 1, bias = 0
  * `no_norm`: (optional) length-`Nf` Boolean indices of features to not be normalized

**Returns:**

  * `train_bias`:  `1` x `Nf` training data biases (means, mins, or zeros)
  * `train_scale`: `1` x `Nf` training data scaling factors (std devs, maxs-mins, or ones)
  * `train`:       `N_train` x `Nf` training   data, normalized
  * `val`:         `N_val`   x `Nf` validation data, normalized
  * `test`:        `N_test`  x `Nf` testing    data, normalized
