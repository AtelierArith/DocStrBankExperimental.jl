```
EigenAnalysis(proj; [maxdim], [pratio])
```

The eigenanalysis of the covariance with a given projection `proj`. Optionally specify the maximum number of dimensions in the output `maxdim` and the percentage of variance to retain `pratio`.

## Projections

  * `:V` - Uncorrelated variables (PCA transform)
  * `:VD` - Uncorrelated variables and variance one (DRS transform)
  * `:VDV` - Uncorrelated variables and variance one (SDS transformation)

The `:V` projection used in the PCA transform projects the data on the eigenvectors V of the covariance matrix.

The `:VD` projection used in the DRS transform. Similar to the `:V` projection, but the eigenvectors are multiplied by the squared inverse of the eigenvalues D.

The `:VDV` projection used in the SDS transform. Similar to the `:VD` transform, but the data is projected back to the basis of the original variables using the Vᵀ matrix.

See [https://geostatisticslessons.com/lessons/sphereingmaf](https://geostatisticslessons.com/lessons/sphereingmaf) for more details about these three variants of eigenanalysis.

# Examples

```julia
EigenAnalysis(:V)
EigenAnalysis(:VD)
EigenAnalysis(:VDV)
EigenAnalysis(:V, maxdim=3)
EigenAnalysis(:VD, pratio=0.99)
EigenAnalysis(:VDV, maxdim=3, pratio=0.99)
```
