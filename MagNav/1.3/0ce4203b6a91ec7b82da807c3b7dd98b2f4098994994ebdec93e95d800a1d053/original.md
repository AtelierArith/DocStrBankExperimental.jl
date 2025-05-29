```
predict_rnn_windowed(m, x, l_window::Int)
```

Apply model `m` to data matrix `x` with sliding window of length-`l_window`.

**Arguments:**

  * `m`:        recurrent neural network model
  * `x`:        `N` x `Nf` data matrix (`Nf` is number of features)
  * `l_window`: temporal window length

**Returns:**

  * `y_hat`: length-`N` prediction vector
