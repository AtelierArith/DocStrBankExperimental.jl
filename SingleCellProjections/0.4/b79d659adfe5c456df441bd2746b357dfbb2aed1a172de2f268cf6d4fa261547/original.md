```
NormalizationModel(data::DataMatrix, design::DesignMatrix;
                   scale=false, min_std=1e-6, annotate=true,
                   rtol=sqrt(eps()), var=:copy, obs=:copy)
```

Create a NormalizationModel based on `data` and a `design` matrix.

  * `scale` - Set to true to normalize variables to unit standard deviation. Can also be set to a vector with a scaling factor for each variable.
  * `min_std` - If `scale==true`, the `scale` vector is set to `1.0 ./ max.(std, min_std)`. That is, `min_std` is used to suppress variables that are very small (and any fluctuations can be assumed to be noise).
  * `annotate` - Only used if `scale!=false`. With `annotate=true`, the `scale` vector is added as a var annotation.
  * `rtol` - Singular values of the design matrix that are `≤rtol` are discarded. Needed for numerical stability.
  * `var` - Can be `:copy` (make a copy of source `var`) or `:keep` (share the source `var` object).
  * `obs` - Can be `:copy` (make a copy of source `obs`) or `:keep` (share the source `obs` object).

See also: [`normalize_matrix`](@ref), [`designmatrix`](@ref)
