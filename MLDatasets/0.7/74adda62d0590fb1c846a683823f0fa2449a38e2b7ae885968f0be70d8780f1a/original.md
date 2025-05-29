```
SVHN2(; Tx=Float32, split=:train, dir=nothing)
SVHN2([Tx, split])
```

The Street View House Numbers (SVHN) Dataset.

  * Authors: Yuval Netzer, Tao Wang, Adam Coates, Alessandro Bissacco, Bo Wu, Andrew Y. Ng
  * Website: http://ufldl.stanford.edu/housenumbers

SVHN was obtained from house numbers in Google Street View images. As such they are quite diverse in terms of orientation and image background. Similar to MNIST, SVHN has 10 classes (the digits 0-9), but unlike MNIST there is more data and the images are a little bigger (32x32 instead of 28x28) with an additional RGB color channel. The dataset is split up into three subsets: 73257 digits for training, 26032 digits for testing, and 531131 additional to use as extra training data.

# Arguments

  * You can pass a specific `dir` where to load or download the dataset, otherwise uses the default one.
  * `split`: selects the data partition. Can take the values `:train`, `:test` or `:extra`.

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
julia> using MLDatasets: SVHN2

julia> using MLDatasets: SVHN2

julia> dataset = SVHN2()
SVHN2:
  metadata    =>    Dict{String, Any} with 2 entries
  split       =>    :train
  features    =>    32×32×3×73257 Array{Float32, 4}
  targets     =>    73257-element Vector{Int64}

julia> dataset[1:5].targets
5-element Vector{Int64}:
 1
 9
 2
 3
 2

julia> dataset.metadata
Dict{String, Any} with 2 entries:
  "n_observations" => 73257
  "class_names"    => ["1", "2", "3", "4", "5", "6", "7", "8", "9", "0"]
```
