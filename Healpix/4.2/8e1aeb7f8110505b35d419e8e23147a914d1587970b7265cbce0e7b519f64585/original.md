```
readFullWeights(filename::String)
```

Read the set of pixel weights used to compute the generalized Fourier transform of a map.

These weights are usually precomputed; you can download the ones available in the [Healpy repository](https://github.com/healpy/healpy-data) using the following command:

```
git clone --depth 1 https://github.com/healpy/healpy-data
```

# Arguments:

  * `filename::String`: filename of the full pixel weights

# Returns:

  * `Vector{Float64}`: contains the compressed pixel weights
