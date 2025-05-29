```
HungarianCorrespondence <: AbstractCorrespondence
```

Use the Hungarian algorithm to assign measuements to blobs. Each measurement is assigned to one blob only. Parameter `p > 0` influences how eager the assignement is on a spectrum between `p ≈ 0` corresponding to nearest neighbor matching, `p = 1` corresponding to minimizing the earth-movers distance, `p → ∞` corresponding to minimizing the maximum error. The default is `p = 1`.

# Parameters

  * `p=1`: the exponent of the cost matrix
  * `dist_th=2`: maximum allowed Mahalanobis distance between a blob and a measurement
