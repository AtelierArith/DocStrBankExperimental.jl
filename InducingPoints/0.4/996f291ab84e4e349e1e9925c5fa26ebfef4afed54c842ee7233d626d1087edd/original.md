```
Greedy(m::Int, s::Int)
```

  * `m` is the desired number of inducing points
  * `s` is the minibatch size on which to select a new inducing point

Greedy approach first proposed by Titsias[1]. Algorithm loops over minibatches of data and select the best ELBO improvement. Requires passing outputs `y`, the `kernel` and the `noise` as keyword arguments to `inducingpoints`.

[1] Titsias, M. Variational Learning of Inducing Variables in Sparse Gaussian Processes. Aistats 5, 567–574 (2009).
