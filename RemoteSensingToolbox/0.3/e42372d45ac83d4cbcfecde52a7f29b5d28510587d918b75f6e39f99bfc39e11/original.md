The Minimum Noise Fraction (MNF) transform is a linear transformation used to reduce the spectral dimensionality of image data and  segregate noise. MNF consists of two separate principal component rotations. The first rotation uses the principal components  of the noise covariance matrix to decorrelate and rescale the noise (a process known as noise whitening), resulting in a transformed  image in which the noise has unit variance and no band-to-band correlations. The second rotation is a standard PCA rotation  applied to the noise-whitened image.

The bands in the transformed image will be ordered according to their Signal to Noise Ratio (SNR), with the highest SNR being  placed first. The result is that the noise becomes concentrated in the higher bands. Thus, the transform can be used to separate  noise from data by performing a forward transform, determining which bands contain coherent images, and running an inverse  transform after either discarding or denoising the remaining bands. The number of bands to keep in the inverse transform can be determined by a number  of methods. The simplest approach is to look at the sorted transformed bands and threshold at the band where no recognizable  features can be observed. An alternative method is to threshold at a desired cumulative SNR.

# Example

```julia-repl
julia> src = DESIS("data/DESIS-HSI-L2A-DT0485529167_001-20220712T223540-V0220")

julia> desis = decode(DESIS, Raster(src, :Bands))

julia> roi = @view desis[X(1019:1040), Y(550:590)];

julia> mnf = fit_mnf(desis, roi)
MNF(dimensions=235) 

Projection Matrix:
235×235 Matrix{Float32}:
 -2.135    2.3502   0.3612   0.5912   0.5217  -0.0917   0.0043  …   0.0002  -0.0001  -0.0004  -0.0004  -0.0      0.0004
 -0.0959   0.0422  -0.0047  -0.2362  -0.3962  -0.2313  -0.1685      0.0001   0.0004   0.0002   0.0003   0.0001  -0.0001
  0.0043   0.0058  -0.0032   0.0023  -0.0061  -0.0048   0.0028     -0.0001   0.0001  -0.0001  -0.0      0.0      0.0001
  0.0039   0.002   -0.002    0.0012  -0.0032  -0.004    0.006      -0.0006   0.0002  -0.0001  -0.0     -0.0003  -0.0
  0.0024   0.0018  -0.003   -0.0008   0.0038  -0.0003   0.0057      0.0009  -0.0007   0.0002  -0.0012   0.0012  -0.0
  0.0019  -0.003    0.0038  -0.002   -0.0001  -0.0003  -0.0     …   0.0021   0.0009  -0.0004   0.0014  -0.0011  -0.0006
  0.0047   0.0055   0.006   -0.0014  -0.0011   0.0021   0.0053     -0.0035   0.0006   0.0002  -0.0026   0.0014   0.0019
  0.0072   0.0042   0.0012   0.0016   0.0011  -0.002   -0.001       0.0     -0.0026   0.0012   0.0034  -0.0006  -0.0009
  ⋮                                            ⋮                ⋱            ⋮                                  
 -0.0004  -0.0012   0.0007   0.0006  -0.0      0.0002   0.0005      0.0005   0.0002  -0.0004  -0.0002  -0.0001   0.0001
 -0.0014  -0.0005  -0.0005   0.0019  -0.0002  -0.0005   0.0017      0.0003   0.0005   0.0      0.0004   0.0005   0.0
 -0.0004   0.0008  -0.0003   0.0013   0.0004   0.0014   0.0004      0.0002  -0.0001   0.0002   0.0001  -0.0002  -0.0002
 -0.0008  -0.0015   0.0021  -0.0004  -0.0004   0.0012   0.0006  …  -0.0011   0.0002  -0.0007   0.0001   0.0005  -0.0001
  0.0008  -0.0004   0.0009   0.0019  -0.0022  -0.0014   0.0013      0.0003  -0.0001  -0.0003  -0.0      0.0003   0.0002
  0.0005   0.0006  -0.0022  -0.0003   0.0     -0.0022   0.0016     -0.001    0.0002  -0.0003   0.0003  -0.0005   0.0005
  0.001   -0.0005  -0.0007   0.0025  -0.0019   0.0005   0.0015      0.0002  -0.0005   0.0     -0.0005   0.0002  -0.0002
 -0.0003   0.0002  -0.0021  -0.0008  -0.0012   0.0003   0.0003     -0.0001  -0.0      0.0001   0.0      0.0      0.0

Component Statistics:
  Eigenvalues: 7975.439  4040.6348  2092.866  717.8178  468.5496  247.5029  202.2003  176.8452  87.3302  ...  0.3602
  Cumulative Eigenvalues: 0.4779  0.72  0.8454  0.8884  0.9165  0.9313  0.9434  0.954  0.9593  ...  1.0
  Explained SNR: 7974.4385  4039.6353  2091.8635  716.8176  467.55  246.5022  201.1985  175.845  86.3301  ...  -0.6399
  Cumulative SNR: 0.4839  0.729  0.856  0.8995  0.9278  0.9428  0.955  0.9657  0.9709  ...  0.9985

julia> transformed = forward_mnf(mnf, desis, 12);

julia> size(transformed)
(1131, 1120, 12)

julia> recovered = inverse_mnf(mnf, transformed);

julia> size(recovered)
(1131, 1120, 235)
```
