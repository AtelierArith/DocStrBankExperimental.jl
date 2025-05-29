```
fastdensesparsemul_outer!(C, a, b, α, β)
```

Fast outer product when computing `C .= β*C + α * a*b'`, but way faster than Base would.

  * `a` is a dense vector (or view), `b` is a sparse vector, `C` is a dense matrix (or view).

Also see `fastdensesparsemul_outer_threaded!` for a multi-threaded version using `Polyester.jl`.
