```
lll_with_removal_transform(x::ZZMatrix, b::ZZRingElem, ctx::LLLContext = LLLContext(0.99, 0.51))
```

Compute a tuple $(r, L, T)$ where the first $r$ rows of $L$ are those remaining from the LLL reduction after removal of vectors with norm exceeding the bound $b$ and $T$ is a transformation matrix so that $L = Tx$.
