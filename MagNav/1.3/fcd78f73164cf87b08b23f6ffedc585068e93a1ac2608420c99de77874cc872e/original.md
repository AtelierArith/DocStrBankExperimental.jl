```
predict_rnn_full(m, x)
```

Apply model `m` to data matrix `x`.

**Arguments:**

  * `m`: recurrent neural network model
  * `x`: `N` x `Nf` data matrix (`Nf` is number of features)

**Returns:**

  * `y_hat`: length-`N` prediction vector
