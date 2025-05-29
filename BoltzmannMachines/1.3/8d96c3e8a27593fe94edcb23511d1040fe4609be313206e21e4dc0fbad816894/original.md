```
updateparameters!(rbm, optimizer)
```

Updates the RBM `rbm` by walking a step in the direction of the gradient that has been computed by calling `computegradient!` on `optimizer`.
