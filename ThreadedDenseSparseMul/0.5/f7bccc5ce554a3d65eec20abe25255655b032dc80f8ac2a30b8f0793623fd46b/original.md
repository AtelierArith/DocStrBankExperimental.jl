```
fastdensesparsemul!(C, A, B, α, β)
```

BLAS like interface, computing `C .= β*C + α*A*B`, but way faster than Base would.

Also see `fastdensesparsemul_threaded!` for a multi-threaded version using `Polyester.jl`.
