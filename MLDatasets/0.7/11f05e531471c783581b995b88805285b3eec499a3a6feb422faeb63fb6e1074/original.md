```
Omniglot(; Tx=Float32, split=:train, dir=nothing)
Omniglot([Tx, split])
```

Omniglot data set for one-shot learning

  * Authors: Brenden M. Lake, Ruslan Salakhutdinov, Joshua B. Tenenbaum
  * Website: https://github.com/brendenlake/omniglot

The Omniglot data set is designed for developing more human-like learning algorithms. It contains 1623 different handwritten characters from 50 different alphabets. Each of the 1623 characters was drawn online via Amazon's Mechanical Turk by 20 different people. Each image is paired with stroke data, a sequences of [x,y,t] coordinates with time (t) in milliseconds.

# Arguments

  * You can pass a specific `dir` where to load or download the dataset, otherwise uses the default one.
  * `split`: selects the data partition. Can take the values `:train`, `:test`, `:small1`, or `:small2`.

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

The images are loaded as a multi-dimensional array of eltype `Tx`. All values will be `0` or `1`. `Omniglot().features` is a 3D array (i.e. a `Array{Tx,3}`), in WHN format (width, height, num_images). Labels are stored as a vector of strings in `Omniglot().targets`. 

```julia-repl
julia> using MLDatasets: Omniglot

julia> dataset = Omniglot(:train)
Omniglot:
  metadata    =>    Dict{String, Any} with 3 entries
  split       =>    :train
  features    =>    105×105×19280 Array{Float32, 3}
  targets     =>    19280-element Vector{Int64}

julia> dataset[1:5].targets
5-element Vector{String}:
 "Arcadian"
 "Arcadian"
 "Arcadian"
 "Arcadian"
 "Arcadian"

julia> X, y = dataset[:];

julia> dataset = Omniglot(UInt8, :test)
Omniglot:
  metadata    =>    Dict{String, Any} with 3 entries
  split       =>    :test
  features    =>    105×105×13180 Array{UInt8, 3}
  targets     =>    13180-element Vector{Int64}
```
