```
CIFAR100(; Tx=Float32, split=:train, dir=nothing)
CIFAR100([Tx, split])
```

The CIFAR100 dataset is a labeled subsets of the 80 million tiny images dataset. It consists of 60000 32x32 colour images in 100 classes and 20 superclasses, with 600 images per class.

Return the CIFAR-100 **trainset** labels (coarse and fine) corresponding to the given `indices` as a tuple of two `Int` or two `Vector{Int}`. The variables returned are the coarse label(s) (`Yc`) and the fine label(s) (`Yf`) respectively.

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
julia> dataset = CIFAR100()
CIFAR100:
  metadata    =>    Dict{String, Any} with 3 entries
  split       =>    :train
  features    =>    32×32×3×50000 Array{Float32, 4}
  targets     =>    (coarse = "50000-element Vector{Int64}", fine = "50000-element Vector{Int64}")

julia> dataset[1:5].targets
(coarse = [11, 15, 4, 14, 1], fine = [19, 29, 0, 11, 1])

julia> X, y = dataset[:];

julia> dataset.metadata
Dict{String, Any} with 3 entries:
  "n_observations"     => 50000
  "class_names_coarse" => ["aquatic_mammals", "fish", "flowers", "food_containers", "fruit_and_vegetables", "household_electrical_devices", "household_furniture", "insects", "large_carnivores", "large_man-made_…
  "class_names_fine"   => ["apple", "aquarium_fish", "baby", "bear", "beaver", "bed", "bee", "beetle", "bicycle", "bottle"  …  "train", "trout", "tulip", "turtle", "wardrobe", "whale", "willow_tree", "wolf", "w…
```
