```
predict_A̅(U, temp, lims::Tuple{F, F}) where {F <: AbstractFloat}
```

Predicts the value of A with a neural network based on the long-term air temperature and on the bounds value to normalize the output of the neural network.

# Arguments

  * `U`: Neural network.
  * `temp`: Temperature to be fed as an input of the neural network.
  * `lims::Tuple{F, F}`: Bounds to use for the affine transformation of the neural   network output.
