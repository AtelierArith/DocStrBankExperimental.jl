Learn Chow Liu Tree(s). It will run on CPU/GPU based on where `train_x` is.

Arguments: 

  * `train_x`: training data. If want gpu, move to gpu before calling this `CuArray(train_x)`.

Keyword arguments:

  * `num_trees=1`: number of trees you want to learned.
  * `dropout_prob=0.0`: drop edges with probability `dropout_prob` when learning maximum spanning tree.
  * `weights=nothing`: weights of samples. Weights are all 1 if `nothing`.
  * `pseudocount=0.0`: add a total of pseudo count spread out overall all categories.
  * `Float=Float64`: precision. `Float32` is faster if `train_x` a large.
