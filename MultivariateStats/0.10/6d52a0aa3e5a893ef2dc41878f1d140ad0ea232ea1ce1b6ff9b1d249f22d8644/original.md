```
ppcaml(Z, mean; ...)
```

Compute probabilistic PCA using on maximum likelihood formulation for a centralized sample matrix `Z`.

*Parameters*:

  * `Z`: a centralized samples matrix
  * `mean`: The mean vector of the **original** samples, which can be a vector of

length `d`, or an empty vector indicating a zero mean.

Returns the resultant [`PPCA`](@ref) model.

**Note:** This function accepts two keyword arguments: `maxoutdim` and `tol`.
