```
lll_with_removal(x::ZZMatrix, b::ZZRingElem, ctx::LLLContext = LLLContext(0.99, 0.51))
```

Compute the LLL reduction of $x$ and throw away rows whose norm exceeds the given bound $b$. Return a tuple $(r, L)$ where the first $r$ rows of $L$ are the rows remaining after removal.
