Performs compressive k-means, but returns a tuple `(C, α)`, where:

  * the columns of `C` are the centroid locations;
  * `α` is a vector of weights used in the reconstruction.

This function accepts the same arguments as [`CKM`](@ref).

See also: [`CKM`](@ref), which returns only the centroids.
