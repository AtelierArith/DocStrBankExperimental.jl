```
LLRRegularization
```

Regularization term implementing the proximal map for locally low rank (LLR) regularization using singular-value-thresholding.

# Arguments

  * `λ`                  - regularization paramter

# Keywords

  * `shape::Tuple{Int}`            - dimensions of the image
  * `blockSize::Tuple{Int}=(2,2)`  - size of patches to perform singular value thresholding on
  * `randshift::Bool=true`         - randomly shifts the patches to ensure translation invariance
  * `fullyOverlapping::Bool=false` - choose between fully overlapping block or non-overlapping blocks
