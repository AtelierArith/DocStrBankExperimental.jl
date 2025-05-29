Algorithm for solving paramateric families of Kolmogorov Equations.

```julia
HighDimPDE.NNKolmogorov(chain, opt)
```

Arguments:

  * `chain`: A Chain neural network with a d-dimensional output.
  * `opt`: The optimizer to train the neural network. Defaults to `ADAM(0.1)`.

[1] Berner Julius et al. "Numerically solving parametric families of high-dimensional Kolmogorov partial differential equations via deep learning."
