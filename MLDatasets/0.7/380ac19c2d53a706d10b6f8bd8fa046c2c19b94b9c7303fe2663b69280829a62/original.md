```
CIFAR10(; Tx=Float32, split=:train, dir=nothing)
CIFAR10([Tx, split])
```

The CIFAR10 dataset is a labeled subsets of the 80 million tiny images dataset. It consists of 60000 32x32 colour images in 10 classes, with 6000 images per class.

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
  * [`convert2image`](@ref) converts features to `RGB` images.

# Examples

```julia-repl
julia> using MLDatasets: CIFAR10

julia> dataset = CIFAR10()
CIFAR10:
  metadata    =>    Dict{String, Any} with 2 entries
  split       =>    :train
  features    =>    32×32×3×50000 Array{Float32, 4}
  targets     =>    50000-element Vector{Int64}

julia> dataset[1:5].targets
5-element Vector{Int64}:
 6
 9
 9
 4
 1

julia> X, y = dataset[:];

julia> dataset = CIFAR10(Tx=Float64, split=:test)
CIFAR10:
  metadata    =>    Dict{String, Any} with 2 entries
  split       =>    :test
  features    =>    32×32×3×10000 Array{Float64, 4}
  targets     =>    10000-element Vector{Int64}

julia> dataset.metadata
Dict{String, Any} with 2 entries:
  "n_observations" => 10000
  "class_names"    => ["airplane", "automobile", "bird", "cat", "deer", "dog", "frog", "horse", "ship", "truck"]
```
