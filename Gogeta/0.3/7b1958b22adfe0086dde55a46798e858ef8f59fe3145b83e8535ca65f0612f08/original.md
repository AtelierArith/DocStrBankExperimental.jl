```
function local_search_CNN(start, cnn_jump; epsilon=0.01, max_iter=10, show_path=false, logging=false, tolerance=0.01)
```

Performs relaxing walk local search on the given convolutional neural network JuMP formulation. See Tong et al. (2024) for more details.

# Parameters

  * `start`: starting point for the search (coordinate in the image space)
  * `cnn_jump`: `JuMP` model containing the CNN formulation

# Optional Parameters

  * `epsilon`: controls the step size taken out of the linear region
  * `max_iter`: maximum number of search steps
  * `show_path`: return the path taken by the local search in addition to the optimum
  * `logging`: print progress info to console
  * `tolerance`: minimum relative improvement required at every step to continue the search
