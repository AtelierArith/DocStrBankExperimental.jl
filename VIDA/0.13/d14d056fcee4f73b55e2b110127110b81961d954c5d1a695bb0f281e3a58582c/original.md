```julia
nxcorr(img1, img2)

```

Returns the normalized cross correlation (NXCORR) between `img1` and `img2`. NXCORR is defined as

```
NXCORR(n, m) = (Nσₙσₘ) Σᵢ (nᵢ - μₙ)(mᵢ - μₘ)
```

where `n` and `m` are the two images `μ` is the mean and `σ` is the pixelwise standard deviation
