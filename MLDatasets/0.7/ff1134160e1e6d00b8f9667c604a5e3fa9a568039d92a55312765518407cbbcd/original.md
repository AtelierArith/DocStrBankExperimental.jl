```
EMNIST(name; Tx=Float32, split=:train, dir=nothing)
EMNIST(name, [Tx, split])
```

The EMNIST dataset is a set of handwritten character digits derived from the NIST Special Database 19 (https://www.nist.gov/srd/nist-special-database-19) and converted to a 28x28 pixel image format and dataset structure that directly matches the MNIST dataset (http://yann.lecun.com/exdb/mnist/). Further information on the dataset contents and conversion process can be found in the paper available at https://arxiv.org/abs/1702.05373v1.

# Arguments

  * `name`: name of the EMNIST dataset. Possible values are: `:balanced, :byclass, :bymerge, :digits, :letters, :mnist`.
  * `split`: selects the data partition. Can take the values `:train` or `:test`.
  * You can pass a specific `dir` where to load or download the dataset, otherwise uses the default one.

# Fields

  * `name`.
  * `split`.
  * `metadata`: A dictionary containing additional information on the dataset.
  * `features`: An array storing the data features.
  * `targets`: An array storing the targets for supervised learning.

# Methods

  * `dataset[i]`: Return observation(s) `i` as a named tuple of features and targets.
  * `dataset[:]`: Return all observations as a named tuple of features and targets.
  * `length(dataset)`: Number of observations.
  * [`convert2image`](@ref) converts features to `Gray` images.

# Examples

The images are loaded as a multi-dimensional array of eltype `Tx`. If `Tx <: Integer`, then all values will be within `0` and `255`,  otherwise the values are scaled to be between `0` and `1`. `EMNIST().features` is a 3D array (i.e. a `Array{Tx,3}`), in WHN format (width, height, num_images). Labels are stored as a vector of integers in `EMNIST().targets`. 

```julia-repl
julia> using MLDatasets: EMNIST

julia> dataset = EMNIST(:letters, split=:train)
EMNIST:
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

julia> dataset = EMNIST(:balanced, Tx=UInt8, split=:test)
EMNIST:
  metadata    =>    Dict{String, Any} with 3 entries
  split       =>    :test
  features    =>    28×28×10000 Array{UInt8, 3}
  targets     =>    10000-element Vector{Int64}
```
