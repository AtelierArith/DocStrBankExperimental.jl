```
lll_gram!(x::ZZMatrix, ctx::LLLContext = LLLContext(0.99, 0.51, :gram))
```

Compute the Gram matrix of an LLL-reduced basis of the lattice given by the Gram matrix $x$ inplace. The matrix $x$ must be symmetric and semidefinite.

By default, the LLL is performed with reduction parameters $\delta = 0.99$ and $\eta = 0.51$. These defaults can be overridden by specifying an optional context object.
