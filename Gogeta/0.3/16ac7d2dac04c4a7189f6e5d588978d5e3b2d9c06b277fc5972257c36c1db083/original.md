```
function optimize_by_walking_CNN!(cnn_jump::JuMP.Model, input; iterations=10, samples_per_iter=5, timelimit=1.0, tolerance=1.0)
```

Performs the full relaxing walk algorithm on the given convolutional neural network JuMP formulation. See Tong et al. (2024) for more details.

# Parameters

  * `cnn_jump`: `JuMP` model containing the CNN formulation.
  * `input`: An example input to the CNN. Used to extract the input dimensions.

# Optional Parameters

  * `iterations`: the number of fresh starts from the linear relaxation (no binary variables fixed)
  * `samples_per_iter`: maximum number of successful samples per iteration
  * `timelimit`: time limit for the LP relaxation solves
  * `tolerance`: how different new samples must be from any previous one
