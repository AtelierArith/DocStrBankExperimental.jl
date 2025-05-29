```
TensorBundle{n,ℙ,g,ν,μ} <: Manifold{n}
```

A manifold representing the space of tensors with a given metric and basis for projection.

Let `n` be the rank of a `Manifold{n}`. The type `TensorBundle{n,ℙ,g,ν,μ}` uses *byte-encoded* data available at pre-compilation, where `ℙ` specifies the basis for up and down projection, `g` is a bilinear form that specifies the metric of the space, and `μ` is an integer specifying the order of the tangent bundle (i.e. multiplicity limit of Leibniz-Taylor monomials). Lastly, `ν` is the number of tangent variables.
