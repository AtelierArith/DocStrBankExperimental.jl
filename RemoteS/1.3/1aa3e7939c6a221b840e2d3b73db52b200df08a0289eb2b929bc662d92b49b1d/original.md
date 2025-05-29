```
I = classify(cube::GItype, model; class_names::Union{String, Vector{String}}="") -> GMTimage
```

  * `cube`: The cube wtih band data to classify.
  * `model`: The trained model obtained from the `train_raster` function.
  * `class_names`: A vector of strings with the class names to be used in the categorical colorbar or a  comma separated single with those class names. The number of class names must match the number used  when training the model with `train_raster`.
