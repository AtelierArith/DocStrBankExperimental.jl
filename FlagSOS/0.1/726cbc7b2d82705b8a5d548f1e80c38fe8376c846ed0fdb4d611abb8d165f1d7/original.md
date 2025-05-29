```
glue(F::HarmonicFlag{T}, G::HarmonicFlag{T}, p::Vector{Int})
```

Glues together the two harmonic Flags `F` and `G`, after applying the permutation `p` to the vertices of `F`. `p` may be a permutation involving more than `size(F)` vertices. Since these Flags describe harmonic densities, the result is another flag of type `F`, where double edges cancelled out.
