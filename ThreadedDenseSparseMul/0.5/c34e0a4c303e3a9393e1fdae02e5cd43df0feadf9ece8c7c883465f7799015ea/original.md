```
fastdensesparsemul!(C, A, B, α, β)
```

Threaded, BLAS like interface, computing `C .= β*C + α*A*B`, but way faster than Base would. Also see `fastdensesparsemul!` for a single-threaded version.
