```
MNIST(; Tx=Float32, split=:train, dir=nothing)
MNIST([Tx, split])
```

The MNIST database of handwritten digits.

  * Authors: Yann LeCun, Corinna Cortes, Christopher J.C. Burges
  * Website: http://yann.lecun.com/exdb/mnist/

MNIST is a classic image-classification dataset that is often used in small-scale machine learning experiments. It contains 70,000 images of handwritten digits. Each observation is a 28x28 pixel gray-scale image that depicts a handwritten version of 1 of the 10 possible digits (0-9).

# Arguments

  * You can pass a specific `dir` where to load or download the dataset, otherwise uses the default one.
  * `split`: selects the data partition. Can take the values `:train` or `:test`.

# Fields

  * `metadata`: A dictionary containing additional information on the dataset.
  * `features`: An array storing the data features.
  * `targets`: An array storing the targets for supervised learning.
  * `split`.

# Methods

  * `dataset[i]`: Return observation(s) `i` as a named tuple of features and targets.
  * `dataset[:]`: Return all observations as a named tuple of features and targets.
  * `length(dataset)`: Number of observations.
  * [`convert2image`](@ref) converts features to `Gray` images.

# Examples

The images are loaded as a multi-dimensional array of eltype `Tx`. If `Tx <: Integer`, then all values will be within `0` and `255`,  otherwise the values are scaled to be between `0` and `1`. `MNIST().features` is a 3D array (i.e. a `Array{Tx,3}`), in WHN format (width, height, num_images). Labels are stored as a vector of integers in `MNIST().targets`. 

```julia-repl
julia> using MLDatasets: MNIST

julia> dataset = MNIST(:train)
MNIST:
  metadata    =>    Dict{String, Any} with 3 entries
  split       =>    :train
  features    =>    28×28×60000 Array{Float32, 3}
  targets     =>    60000-element Vector{Int64}

julia> dataset[1:5].targets
5-element Vector{Int64}:
7
2
1
0
4

julia> X, y = dataset[:];

julia> dataset = MNIST(UInt8, :test)
MNIST:
  metadata    =>    Dict{String, Any} with 3 entries
  split       =>    :test
  features    =>    28×28×10000 Array{UInt8, 3}
  targets     =>    10000-element Vector{Int64}
```
