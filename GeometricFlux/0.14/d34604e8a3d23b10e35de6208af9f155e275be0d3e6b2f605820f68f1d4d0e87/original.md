```
VariationalGraphEncoder(nn, h_dim, z_dim)
```

Variational graph encoder layer.

# Arguments

  * `nn`: neural network. It can be any graph convolutional layer.
  * `h_dim`: dimension of hidden layer. This should fit the output dimension of `nn`.
  * `z_dim`: dimension of latent variable layer. This will be parametrized into `μ` and `logσ`.

Encoder can be any graph convolutional layer.
