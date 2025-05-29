```
subsample_random(X::AbstractAlignment, m::Int)
```

Return an `Alignment` with `m` sequences taking randomly from `X`. Sampling is done without replacement, meaning the `m` sequences are all at different positions in `X`.
