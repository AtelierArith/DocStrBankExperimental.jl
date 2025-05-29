```
ImageNet(; split=:train, dir=nothing, kwargs...)
ImageNet([split])
```

The ImageNet 2012 Classification Dataset (ILSVRC 2012-2017).

This is the most highly-used subset of ImageNet. It spans 1000 object classes and contains 1,281,167 training images, 50,000 validation images and 100,000 test images. By defaults, each image is in `224 × 224 × 3` format in RGB color space. This can be changed by modifying the preprocessor `transform`.

# Arguments

  * You can pass a specific `dir` where to load or download the dataset, otherwise uses the default one.
  * `train_dir`, `val_dir`, `test_dir`, `devkit_dir`: optional subdirectory names of `dir`.   Default to `"train"`, `"val"`, `"test"` and `"devkit"`.
  * `split`: selects the data partition. Can take the values `:train:`, `:val` and `:test`.   Defaults to `:train`.
  * `transform`: preprocessor applied to convert an image file to an array.   Assumes a file path as input and an array in WHC format as output.   Defaults to [`CenterCropNormalize`](@ref), which applies a center-cropping view   and normalization using coefficients from PyTorch's vision models.

# Fields

  * `split`: Symbol indicating the selected data partition
  * `transform`: Preprocessing pipeline. Can be configured to select output dimensions and type.
  * `paths`: paths to ImageNet images
  * `targets`: An array storing the targets for supervised learning.
  * `metadata`: A dictionary containing additional information on the dataset.

Also refer to [`AbstractTransform`](@ref), [`CenterCropNormalize`](@ref).

# Methods

  * `dataset[i]`: Return observation(s) `i` as a named tuple of features and targets.
  * `dataset[:]`: Return all observations as a named tuple of features and targets.
  * `length(dataset)`: Number of observations.
  * [`convert2image`](@ref) converts features to `RGB` images.

# Examples

```julia-repl
julia> using ImageNetDataset

julia> dataset = ImageNet(:val);

julia> dataset[1:5].targets
5-element Vector{Int64}:
 1
 1
 1
 1
 1

julia> X, y = dataset[1:5];

julia> size(X)
(224, 224, 3, 5)

julia> X, y = dataset[2000];

julia> convert2image(dataset, X)

julia> dataset.metadata
Dict{String, Any} with 4 entries:
  "class_WNIDs"       => ["n01440764", "n01443537", "n01484850", "n01491361", "n01494475", …
  "class_description" => ["freshwater dace-like game fish of Europe and western Asia noted …
  "class_names"       => Vector{SubString{String}}[["tench", "Tinca tinca"], ["goldfish", "…
  "wnid_to_label"     => Dict("n07693725"=>932, "n03775546"=>660, "n01689811"=>45, "n021008…

julia> dataset.metadata["class_names"][y]
  3-element Vector{SubString{String}}:
   "common iguana"
   "iguana"
   "Iguana iguana"
```

# References

[1]: [Russakovsky et al., ImageNet Large Scale Visual Recognition Challenge](https://arxiv.org/abs/1409.0575)
