```
project(M::AbstractProjectiveSpace, p)
```

Orthogonally project the point `p` from the embedding onto the [`AbstractProjectiveSpace`](@ref) `M`:

$$
\operatorname{proj}(p) = \frac{p}{\lVert p \rVert}_{\mathrm{F}},
$$

where $\lVert ⋅ \rVert_{\mathrm{F}}$ denotes the Frobenius norm. This is identical to projection onto the [`AbstractSphere`](@ref).
