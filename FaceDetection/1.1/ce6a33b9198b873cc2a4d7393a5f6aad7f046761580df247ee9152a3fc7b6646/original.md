```
determine_feature_size(
    pictures::Vector{String}
) -> Tuple{Integer, Integer, Integer, Integer, Tuple{Integer, Integer}}
determine_feature_size(
    pos_training_path::String,
    neg_training_path::String
) -> Tuple{Integer, Integer, Integer, Integer, Tuple{Integer, Integer}}
```

Takes images and finds the best feature size for the image size.

# Arguments

  * `pictures::Vector{String}`: a list of paths to the images

OR

  * `pos_training_path::String`: the path to the positive training images
  * `neg_training_path::String`: the path to the negative training images

# Returns

  * `max_feature_width::Integer`: the maximum width of the feature
  * `max_feature_height::Integer`: the maximum height of the feature
  * `min_feature_height::Integer`: the minimum height of the feature
  * `min_feature_width::Integer`: the minimum width of the feature
  * `min_size_img::Tuple{Integer, Integer}`: the minimum-sized image in the image directories
