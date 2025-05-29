```
ensemble_vote_all(images::Vector{String}, classifiers::Vector{HaarLikeObject}) -> Vector{Int8}
ensemble_vote_all(image_path::String, classifiers::Vector{HaarLikeObject})     -> Vector{Int8}
```

Given a path to images, loads images then classifies votes using given classifiers.  I.e., if the sum of all classifier votes is greater 0, the image is classified positively (1); else it is classified negatively (0). The threshold is 0, because votes can be +1 or -1.

# Arguments

  * `images::Vector{String}`: list of paths to images; OR `image_path::String`: Path to images dir
  * `classifiers::Vector{HaarLikeObject}`: List of classifiers

# Returns

`votes::Vector{Int8}`: A list of assigned votes (see ensemble_vote).
