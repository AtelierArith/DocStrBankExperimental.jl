```
remove(z::FracElem{T}, p::T) where {T <: RingElem}
```

Return the tuple $n, x$ such that $z = p^nx$ where $x$ has valuation $0$ at $p$.
