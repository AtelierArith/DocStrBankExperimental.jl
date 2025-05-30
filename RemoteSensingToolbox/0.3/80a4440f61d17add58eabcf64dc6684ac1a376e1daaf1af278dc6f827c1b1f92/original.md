Remotely sensed imagery typically consists of anywhere from four to several hundred spectral bands. These bands are often highly correlated due to occupying similar spectral regions. Principal Component Analysis (PCA) is used in remote sensing to:

1. Create a smaller dataset from multiple bands, while retaining as much of the original spectral information as possible. The new image will consist of several uncorrelated PC bands.
2. Reveal complex relationships among spectral features.
3. Distinguish between characteristics that are prevalent in most bands and those that are specific to only a few.

# Example

```julia-repl
julia> desis = DESIS("DESIS-HSI-L2A-DT0884573241_001-20200601T234520-V0210/");

julia> desis_bands = Raster(desis, :Bands)

julia> pca = fit_pca(desis_bands, stats_fraction=0.1)
PCA(dimensions=235) 

Projection Matrix:
235×235 Matrix{Float32}:
  0.0001  0.0032   0.0016  -0.0094   0.0147  -0.0151  -0.0049   0.0163  …   0.0038  -0.0012   0.0008  -0.0032  -0.0007   0.0053
  0.0005  0.0099   0.0042  -0.0244   0.0517  -0.0335  -0.0185   0.0441     -0.0023  -0.0016  -0.0008   0.001    0.0003  -0.0004
  0.0003  0.015    0.0053  -0.037    0.133   -0.0443  -0.0271   0.1381     -0.0006   0.0004   0.0002  -0.0006   0.0003   0.0002
  0.0003  0.019    0.0071  -0.0385   0.1369  -0.0393  -0.0148   0.0949     -0.0008   0.0006  -0.0001  -0.0006   0.0001  -0.0006
  0.0003  0.0232   0.0073  -0.0419   0.1469  -0.037    0.0041   0.0839     -0.0013  -0.0025   0.0005   0.0007   0.0007  -0.0002
  0.0001  0.0267   0.0077  -0.0461   0.1713  -0.0325   0.0246   0.0861  …   0.0013  -0.0007  -0.0007   0.0024  -0.0012  -0.0028
  0.0001  0.0295   0.0083  -0.0476   0.1695  -0.0348   0.0319   0.0827     -0.0015  -0.0016  -0.0029   0.0004   0.0019  -0.0009
 -0.0001  0.0318   0.0086  -0.0482   0.17    -0.0352   0.0414   0.0784      0.0005  -0.002    0.0003   0.0021  -0.0003  -0.0022
  ⋮                                           ⋮                         ⋱            ⋮                                  
 -0.0663  0.0371  -0.1728   0.0196  -0.0508  -0.1394  -0.0054  -0.0226     -0.0003   0.0001   0.0007  -0.0009  -0.0002   0.0004
 -0.0658  0.0365  -0.1679   0.0204  -0.0717  -0.1474  -0.0087  -0.0193     -0.0006   0.0002   0.0004  -0.0      0.0004  -0.0001
 -0.0655  0.0352  -0.163    0.0193  -0.0767  -0.1511  -0.012   -0.0232     -0.0005   0.0002  -0.0004  -0.0001  -0.0002   0.0005
 -0.066   0.035   -0.1618   0.0193  -0.0859  -0.1503  -0.0055  -0.0177  …   0.0003   0.0005   0.001   -0.0      0.0003  -0.0002
 -0.067   0.035   -0.1619   0.019   -0.0745  -0.1466   0.0245  -0.0228     -0.0001   0.0002  -0.0002  -0.0001  -0.0002   0.0005
 -0.0679  0.0343  -0.1601   0.0176  -0.0721  -0.139    0.0328  -0.0286      0.0003   0.0003   0.0005  -0.0      0.0003   0.0002
 -0.0682  0.0337  -0.1588   0.0151  -0.0458  -0.1242   0.0549  -0.0315      0.0002  -0.0002  -0.0003   0.0002  -0.0003  -0.0005
 -0.0711  0.0343  -0.1601   0.012   -0.0612  -0.1804   0.2151  -0.0971      0.0004  -0.0001   0.0      0.0003   0.0     -0.0003

Importance of Components:
  Cumulative Variance: 0.8782  0.9493  0.9809  0.9869  0.9889  0.9906  0.9915  0.9922  0.9928  ...  1.0
  Explained Variance: 0.8782  0.0711  0.0316  0.006  0.0021  0.0017  0.0009  0.0007  0.0006  ...  0.0

julia> transformed = forward_pca(pca, desis_bands, 12);

julia> size(transformed)
(1131, 1120, 12)

julia> recovered = inverse_pca(pca, transformed);

julia> size(recovered)
(1131, 1120, 235)
```
