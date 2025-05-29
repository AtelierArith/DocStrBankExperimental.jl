```
lll_gram_with_transform(x::ZZMatrix, ctx::LLLContext = LLLContext(0.99, 0.51, :gram))
```

Return a tuple $(L, T)$ where $L$ is the Gram matrix of an LLL-reduced basis of the lattice given by the Gram matrix $x$ and $T$ is a transformation matrix with $L = T^\top x T$. The matrix $x$ must be symmetric and non-singular.

See [`lll_gram`](@ref) for the used default parameters which can be overridden by supplying an optional context object.
