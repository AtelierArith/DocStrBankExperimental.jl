Algorithm for solving Kolmogorov Equations.

```julia
HighDimPDE.NNKolmogorov(chain, opt)
```

Arguments:

  * `chain`: A Chain neural network with a d-dimensional output.
  * `opt`: The optimizer to train the neural network. Defaults to `ADAM(0.1)`.

[1]Beck, Christian, et al. "Solving stochastic differential equations and Kolmogorov equations by means of deep learning." arXiv preprint arXiv:1806.00421 (2018).
