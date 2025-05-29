```
NxCorr(img::IntensityMap)
```

Construct the normalized cross correlation (NXCORR) divergence with respect to the image `img`. To maximize the NXCorr we instead compute the -log(|NxCorr|) as the divergence

NxCorr is defined as:     NXCORR(n, m) = (Nσₙσₘ) Σᵢ (nᵢ - μₙ)(mᵢ - μₘ) where `n` and `m` are the two images `μ` is the mean and `σ` is the pixelwise standard deviation
