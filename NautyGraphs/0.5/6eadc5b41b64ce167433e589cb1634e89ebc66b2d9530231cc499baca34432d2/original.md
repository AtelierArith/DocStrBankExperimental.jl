```
ghash(g::AbstractNautyGraph)
```

Hash the canonical version of `g`, so that (up to hash collisions) `ghash(g1) == ghash(g2)` implies `is_isomorphic(g1, g2) == true`. Hashes are computed using `Base.hash` for small graphs (nv < 8192), or using the first 64 bits of `sha256` for larger graphs.
