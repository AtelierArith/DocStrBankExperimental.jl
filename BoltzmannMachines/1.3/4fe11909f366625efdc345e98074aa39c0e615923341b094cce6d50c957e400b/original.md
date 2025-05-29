```
trainrbm!(rbm, x)
```

Trains the given `rbm` for one epoch using the data set `x`. (See also function `fitrbm`.)

# Optional keyword arguments:

  * `learningrate`, `cdsteps`, `sdlearningrate`, `upfactor`, `downfactor`,  `optimizer`:  See documentation of function `fitrbm`.
  * `chainstate`: a matrix for holding the states of the RBM's hidden nodes. If  it is specified, PCD is used.
