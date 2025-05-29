```
hamming_distance(vector1::Array{Float64, 1}, vector2::Array{Float64, 1},
                 threshold::Float64 = 0.5)::Float64
```

Compute the [Hamming distance](https://en.wikipedia.org/wiki/Hamming_distance) between two vectors. It takes a `threshold` parameter to "binarize" the vectors. For instance, if `threshold = 0.7`, all values larger than or equal to 0.7 will be considerd `1.0`, otherwise `0.0`.

!!! note
    This function may be more appropriated to threshold/direct chromosome representations.


# Arguments

  * `vector1::Array{Float64, 1}`: the first vector.
  * `vector2::Array{Float64, 1}`: the second vector.
  * `threshold::Float64 = 0.5`: the threshold for binarization.

# Throws

  * `ArgumentError`: if `vector1` and `vector2` have different sizes.
