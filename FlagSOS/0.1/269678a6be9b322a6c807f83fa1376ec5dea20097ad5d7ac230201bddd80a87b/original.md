```
glue(F::T, G::T, p::Vector{Int})::U where {T<:Flag, U<:Flag}
```

Glues together the two Flags `F` and `G`, after applying the permutation `p` to the vertices of `F`. `p` may be a permutation involving more than `size(F)` vertices, in which case the result should have at least `maximum(p)` vertices. Optionally specifices a different output Flag type, for cases where the internal Flag type differs and there are performance advantages (such as the case of internal non-induced Graphs and the gluing of two induced Graphs).
