```
denorm_sets(train_bias, train_scale, train, val, test)
```

Denormalize (or destandardize) features (columns) of training, validation, & testing data.

**Arguments:**

  * `train_bias`:  `1` x `Nf` training data biases (means, mins, or zeros)
  * `train_scale`: `1` x `Nf` training data scaling factors (std devs, maxs-mins, or ones)
  * `train`:       `N_train` x `Nf` training   data, normalized
  * `val`:         `N_val`   x `Nf` validation data, normalized
  * `test`:        `N_test`  x `Nf` testing    data, normalized

**Returns:**

  * `train`: `N_train` x `Nf` training   data, denormalized
  * `val`:   `N_val`   x `Nf` validation data, denormalized
  * `test`:  `N_test`  x `Nf` testing    data, denormalized
