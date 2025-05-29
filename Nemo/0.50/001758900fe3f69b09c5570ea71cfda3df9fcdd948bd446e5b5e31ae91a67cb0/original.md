```
lll_gram(x::ZZMatrix, ctx::LLLContext = LLLContext(0.99, 0.51, :gram))
```

Return the Gram matrix $L$ of an LLL-reduced basis of the lattice given by the Gram matrix $x$. The matrix $x$ must be symmetric and semidefinite. If an indefinite matrix is provided, the output is undefined.

By default, the LLL is performed with reduction parameters $\delta = 0.99$ and $\eta = 0.51$. These defaults can be overridden by specifying an optional context object.
