```
n_exclusive_jets(clusterseq::ClusterSequence; dcut::AbstractFloat)
```

Return the number of exclusive jets of a ClusterSequence that are above a certain dcut value.

# Arguments

  * `clusterseq::ClusterSequence`: The `ClusterSequence` object containing the clustering history.
  * `dcut::AbstractFloat`: The maximum value for the distance parameter in the reconstruction.

# Returns

The number of exclusive jets in the `ClusterSequence` object.

# Example

```julia
n_exclusive_jets(clusterseq, dcut = 20.0)
```
