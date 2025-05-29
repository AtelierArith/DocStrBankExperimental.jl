Unitarity of a matrix.

```
pop_loss = 1 - unitarity(U)
```

measures the loss of population from the subspace described by `U`. E.g., for a two-qubit gate, `U` is a 4×4 matrix. The `unitarity` is defined as $\Re[\tr(Û^†Û) / N]$ where $N$ is the dimension of $Û$.
