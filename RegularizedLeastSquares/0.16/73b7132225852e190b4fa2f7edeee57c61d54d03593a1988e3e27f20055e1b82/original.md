```
    PlugAndPlayRegularization
```

Regularization term implementing a given plug-and-play proximal mapping. The actual regularization term is indirectly defined by the learned proximal mapping and as such there is no `norm` implemented.

# Arguments

  * `λ`                  - regularization paramter

# Keywords

  * `model`       - model applied to the image
  * `shape`       - dimensions of the image
  * `input_transform` - transform of image before `model`
