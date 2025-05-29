```
pointwise_dimensions(X::StateSpaceSet, εs::AbstractVector; kw...) → Δloc
```

Return the pointwise dimensions for each point in `X`, i.e., the exponential scaling of the inner correlation sum

$$
c_q(\epsilon) = \left[\sum_{j:|i-j| > w} B(||X_i - X_j|| < \epsilon)\right]^{q-1}
$$

versus $\epsilon$. `Δloc[i]` is the exponential scaling (deduced by a call to [`linear_region`](@ref)) of $c_q$ versus $\epsilon$ for the `i`th point of `X`.

Keywords are the same as in [`correlationsum`](@ref). To obtain the inner correlation sums without doing the exponential scaling fit use `FractalDimensions.pointwise_correlationsums` with same inputs.
