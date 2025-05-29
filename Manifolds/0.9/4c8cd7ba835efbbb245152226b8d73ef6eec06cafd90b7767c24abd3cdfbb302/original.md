```
project(M::AbstractProjectiveSpace, p, X)
```

Orthogonally project the point `X` onto the tangent space at `p` on the [`AbstractProjectiveSpace`](@ref) `M`:

$$
\operatorname{proj}_p (X) = X - p⟨p, X⟩_{\mathrm{F}},
$$

where $⟨⋅, ⋅⟩_{\mathrm{F}}$ denotes the Frobenius inner product. For the real [`AbstractSphere`](@ref) and `AbstractProjectiveSpace`, this projection is the same.
