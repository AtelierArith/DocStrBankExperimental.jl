```
fastdensesparsemul_outer_threaded!(C, a, b, α, β)
```

Threaded, fast outer product when computing `C .= β*C + α * a*b'`, but way faster than Base would, using `Polyester.jl`.

  * `a` is a dense vector (or view), `b` is a sparse vector, `C` is a dense matrix (or view).

Also see `fastdensesparsemul_outer!` for a single-threaded version.
